# Proyecto de Predicción de Abandono de Clientes (Churn Analysis) 

Este repositorio contiene la fase de Modelado Predictivo y Estrategia de Retención. El objetivo principal es utilizar algoritmos de Machine Learning para identificar de manera proactiva a los clientes con alta probabilidad de cancelar su servicio, permitiendo implementar intervenciones comerciales basadas en datos.

---

## Herramientas y Tecnologías Utilizadas

El desarrollo de esta fase se realizó dentro del ecosistema de Ciencia de Datos en Python, utilizando las siguientes librerías y herramientas:

### Análisis y Manipulación de Datos
- **Pandas** y **NumPy**: Estructuración de DataFrames, transformación de variables y operaciones matriciales necesarias para el entrenamiento de modelos.

### Machine Learning (Scikit-Learn e Imbalanced-Learn)
- `train_test_split`: División estratégica del dataset (80/20) con estratificación para preservar la proporción de clases.
- `StandardScaler`: Normalización de variables numéricas para garantizar estabilidad y convergencia en modelos lineales.
- `SMOTE`: Balanceo de la clase minoritaria mediante generación de ejemplos sintéticos.
- Algoritmos implementados:
  - `LogisticRegression` (modelo lineal base).
  - `RandomForestClassifier` (modelo de ensamble basado en árboles).

### Visualización y Entorno de Desarrollo
- **Seaborn** y **Matplotlib**: Generación de matrices de confusión, mapas de calor e importancia de variables.
- **Google Colab**: Entorno de ejecución en la nube basado en Jupyter Notebooks.

---

## Metodología Aplicada

### 1. Preparación y Balanceo

Dado que únicamente el 26,5% de los clientes cancelan el servicio, se aplicó SMOTE exclusivamente sobre el conjunto de entrenamiento. Este enfoque evitó el sesgo hacia la clase mayoritaria y previno problemas de data leakage hacia el conjunto de prueba.

### 2. Evaluación de Desempeño

Los modelos fueron comparados utilizando métricas de clasificación con especial énfasis en el Recall de la clase 1 (clientes que cancelan), ya que el objetivo estratégico es maximizar la detección de fugas reales.

| Métrica | Regresión Logística (Escalada) | Random Forest |
|----------|--------------------------------|---------------|
| Accuracy | 78% | 77% |
| Recall (Clase 1) | 0.62 | 0.56 |
| F1-Score | 0.59 | 0.57 |

---

## Diagnóstico de los Modelos

### Regresión Logística (Modelo Seleccionado)

Presenta un comportamiento equilibrado:
- Accuracy en entrenamiento: 83,5%.
- Accuracy en prueba: 77,6%.

La diferencia moderada entre ambos valores indica adecuada capacidad de generalización y estabilidad ante datos nuevos.

### Random Forest

Presenta un caso de overfitting significativo:
- Accuracy en entrenamiento: 99,8%.

Este comportamiento sugiere que el modelo memorizó los datos de entrenamiento en lugar de capturar patrones generalizables, reduciendo su utilidad en escenarios reales.

---

## Factores Críticos Identificados

A partir del análisis de coeficientes y de la importancia de variables, se identificaron los siguientes impulsores principales de la cancelación:

### Antigüedad (Tenure)
Los clientes con menos de 6 meses de servicio presentan mayor probabilidad de abandono.

### Cargos Mensuales
El costo mensual es uno de los factores más influyentes en la decisión de cancelar.

### Tipo de Internet
Los usuarios de Fibra Óptica muestran una tasa de cancelación superior a la esperada, lo que sugiere posibles problemas de percepción de valor o precio.

---

## Estrategias de Retención Propuestas

### Migración de Contratos
Incentivar el cambio de contratos "Mes a Mes" hacia planes anuales o bianuales mediante beneficios económicos.

### Programa de Onboarding
Fortalecer la experiencia del cliente durante los primeros seis meses de servicio para reducir la tasa de abandono temprana.

### Optimización de Métodos de Pago
Promover el uso de Débito Automático en reemplazo del Cheque Electrónico para reducir volatilidad y mejorar retención.

---

## Instrucciones de Ejecución

1. Cargar el dataset original en la sección correspondiente.
2. Ejecutar las celdas de preprocesamiento (limpieza y One-Hot Encoding).
3. Ejecutar la sección de modelado para generar métricas comparativas y visualizaciones de importancia de variables.
