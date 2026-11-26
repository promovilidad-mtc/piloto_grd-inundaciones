# Piloto de Mapeo de Áreas y Vías Inundables — Ciudad de Tumbes

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/TU-USUARIO/piloto-inundaciones-tumbes/blob/main/piloto_tumbes_unspider.ipynb)

Repositorio reproducible para la detección satelital de áreas inundables y el análisis de exposición de la red vial urbana en la ciudad de **Tumbes, Perú** (caso piloto: evento de lluvias extremas de marzo de 2023).

## Metodología

El flujo de trabajo integra dos estándares internacionales abiertos y reproducibles:

1. **Detección de huella de inundación (UN-SPIDER / ONU):**
   - Implementación en Google Earth Engine (GEE) basada en la práctica recomendada *Radar-based Flood Mapping* de **UN-SPIDER** (*United Nations Platform for Space-based Information for Disaster Management and Emergency Response*).
   - Comparación multitemporal de imágenes de radar de apertura sintética **Sentinel-1 GRD** (polarización `VV`, modo `IW`, órbita descendente) entre un periodo seco de referencia (`2023-01-01` a `2023-02-25`) y el periodo del evento (`2023-03-08` a `2023-03-25`).
   - Aplicación de filtro *speckle* (`50 m`), ratio de cambio (`> 1.25`) y enmascaramiento de cuerpos de agua permanentes (*JRC Global Surface Water*) y pendientes mayores a `5°` (*SRTM 30m*).

2. **Análisis de exposición de infraestructura vial (Enfoque BID — Fase 1 Screening):**
   - Extracción de la red vial urbana desde OpenStreetMap (`osmnx`) y cruce espacial (`geopandas.overlay`) en proyección oficial **WGS 84 / UTM zona 17S (`EPSG:32717`)** siguiendo los lineamientos de *Screening de Exposición* de la **Metodología de Evaluación del Riesgo de Desastres y Cambio Climático para Proyectos del BID** (Barandiarán et al., BID).

## Estructura del Repositorio

```text
piloto-inundaciones-tumbes/
├── piloto_tumbes_unspider.ipynb   # Notebook completo ejecutable en Google Colab
├── requirements.txt               # Dependencias mínimas de Python
└── README.md                      # Documentación metodológica y resultados
```

## Resultados del Piloto (Tumbes — Marzo 2023)

*(Nota: Ejecuta el notebook `piloto_tumbes_unspider.ipynb` para actualizar esta tabla con los valores exactos generados para tu polígono y sube el archivo resultante `tumbes_inundacion_2023.gpkg` a este repositorio).*

| Jerarquía Vial (`highway`) | Longitud Expuesta (km) |
| :--- | :---: |
| `residential` | *Pendiente de ejecución* |
| `tertiary` | *Pendiente de ejecución* |
| `secondary` | *Pendiente de ejecución* |
| `primary` | *Pendiente de ejecución* |
| `unclassified` | *Pendiente de ejecución* |

## Referencias Oficiales

- **UN-SPIDER (ONU):** *Recommended Practice: Radar-based Flood Mapping*. United Nations Office for Outer Space Affairs (UNOOSA). Disponible en: [un-spider.org](https://www.un-spider.org/advisory-support/recommended-practices/recommended-practice-radar-based-flood-mapping)
- **Banco Interamericano de Desarrollo (BID):** Barandiarán, M., Esquivel, M., Lacambra, S., Suárez, G., & Zuloaga, D. (2019). *Metodología de evaluación del riesgo de desastres y cambio climático para proyectos del BID*. Documento técnico IDB-TN-1636.
