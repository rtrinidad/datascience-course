---
title       : Inferencia Estadística
subtitle    : Curso de Data Science con Impacto Social
author      : Jorge Saldivar
job         : Universidad Católica "Nuestra Señora de la Asunción"
logo        : logo-uca.png
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
url:
  lib: ../libraries
  assets: ../assets
widgets     : [mathjax]     # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---



<style type="text/css">
code.r{ /* Code block */
    font-size: 18px;
}
pre { /* Code block - determines code spacing between lines */
    font-size: 16px;
}
</style>

## Análisis Inferencial

* El análisis infencial se utiliza para derivar, por medio de modelos estadísticos, conclusiones respecto a un conjunto de datos

* La idea es probar si los datos con los que contamos proveen suficientes evidencias para comprobar ciertas afirmaciones sobre un fenómeno a estudiar

* La fortaleza de la conclusión depende de como los datos fueron colectados

<img class=center src="../assets/img/analisis_inferencial.png" height=300 />

---

## Test de Hipótesis

* De las diferentes técnicas del análisis inferencial, nos enfocamos en el **Test de Hipótesis**

* El **Test de Hipótesis** (o también conocido como **Prueba Estadística**) es un método del análisis inferencial que sirve para determinar, por ejemplo, si la diferencia entre dos grupos es estadísticamente significativa

* Ayuda a responder preguntas como, ¿es la diferencia encontrada fruto del azar?, o ¿que tan probable es que la diferencia esté reflejando alguna diferencia real entre los dos grupos?

<img class=center src="../assets/img/conclusion_analisis_inferencial.png" height=300 />

---

## Proceso de Test de Hipótesis

* El test de hipótesis es parecido a una demostración por contradicción en matemáticas

* Empezamos por asumir algo contrario a lo que queremos probar y la idea es demostrar en el proceso que nuestra asunción inicial es incorrecta. Analogía: **juicios orales**

* **Ejemplo BECAL**. Queremos probar que existe una diferencia entre la cantidad de becas otorgadas a gente del interior es diferente a la cantidad de becas otorgadas a gente de la capital. 

  - **Hipótesis NULA (H0)**: no existe diferencia entre la cantidad de becas otorgadas a gente del interior con respecto a gente de la capital (asunción inical)
  
  - **Hipótesis alternativa (HA)**: si existe una diferencia entre la cantidad de becas otorgadas a gente del interior con respecto a gente de la capital (lo que nos interesa saber)

* Lo que hacemos entonces es usar métodos estadísticos para verificar si los datos a mano proveen evidencias suficientes que nos permitan rechazar H0 en favor de HA.

* Toda respuesta en estadística tiene siempre cierto grado de incertidumbre, por la variabilidad natural de los datos. Por lo tanto lo que realmente demostramos es que es **"muy probable"** que H0 es falso (o verdadero)

---

## Tipos de hipótesis alternativas

* Éxisten dos tipos de hipótesis alternativas

* Cuando en la hipótesis no hacemos referencia a el sentido de la diferencia, es decir solo nos interesa saber si existe o no una diferencia, decimos que estamos trabajando con una **hipótesis bi-direccional**

  * **Ejemplo.** Existe una diferencia en la cantidad de becas que reciben los del interior y la capital

* Cuando en la hipótesis si hacemos referencia a que la diferencia es mayor o menos, decimos que estamos trabajando con una **hipótesis uni-direccional**

  * **Ejemplo.** Los del interior reciben **menos** (o **más**) becas que los de la capital

---

## Prueba Estadística

* Luego de definir las hipótesis, el siguiente consiste en recolectar evidencias que nos permitan comprobar nuestras hipótesis

* En un test de hipótesis la manera de "recolectar evidencias" es aplicando a los datos **pruebas estadísticas**

* La diferencia entre una prueba estadística y cualquier otro procedimiento estadístico es que la prueba estadística está formulada asumiendo que H0, la hipótesis nula, es verdadera

* Es decir, en un test de hipótesis definimos nuestra hipótesis y después trabjamos asumiendo que H0 es verdadera

<img class=center src="../assets/img/evidence.png" height=250 />

---

## P-value y significancia estadística

* Luego de colectar las evidencias llega el momento de la deliberar si las mismas son suficientes para rechazar nuestra hipótesis nula (H0)

* En estadística la herramienta que se utiliza en la deliberación se llama **P-value**. El **p-value** transforma una prueba estadística a una escala probabilística

* **P-value** es un número entre 0 y 1 que cuantifica la solidez de las evidencias en contra de la hipótesis nula (H0)

* Cuanto más pequeño el **p-value** más sólidas las evidencias en contra de la hipótesis nula (H0)

* Lo que el **p-value** nos dice es que tan probable serían los resultados de la prueba estadística si la hipótesis nula (H0) fuera verdad

* Si la evidencias son lo "suficientemente sólidas", es decir si tenemos un **p-value** pequeño, decimos que la pruba estadística es **estadísticamente significativa**

---

## Nivel de significancia alpha 

* La pregunta ahora es como determinamos que un **p-value** es pequeño. Es ¿0,5 pequeño?, ¿es 0,01 pequeño?

* Necesitamos una referencia contra la cual comparar nuestro **p-value**

* A este valor referencial, o nivel de significancia, se le llama **alpha** y su definición es bastante arbitraria aunque en general se establece **0,05** como valor estándar

* Entonces se dice que si el **p-value es menor a alpha** los datos a mano aportan evidencias suficientes para rechazar la hipótesis H0 en favor de HA

* También el nivel de significancia indica como se va a desempeñar la prueba estadística si se realiza repetidamente con diferentes muestras del mismo tamaño. Por ejemplo, un nivel de significancia alpha de 0,05 indica que solo en el 5% de los casos rechazaremos la hipótesis nula H0 de manera equivocada

---

## Poder estadístico de la prueba

* El poder estadístico de una prueba es la probabilidad de tomar la decisión correcta (rechazar la hipótesis nula H0) cuando la hipótesis nula H0 es falsa (error del Tipo I, falso negativo)

* Cuanto más poder tiene una prueba estadística más sensible es a detectar correctamente hipótesis nula H0 falsas

* Esto muestra que conviene siempre elegir niveles de significancia alpha bajos

* Sin embargo, cuando la cantidad de datos a mano es poca niveles de significancia alpha muy bajos nos pueden llevar a cometer errores del Tipo II (falso positivo) debido a que la prueba estadística no tiene suficiente poder

---

## T-test y la distrubción T

* En los tests de hipótesis, la herramienta que frecuentemente se utiliza para realizar análisis de significancia es el **t-test**

* El t-test se vale de la **distribución t** (o también llamada student's t) que se usa para aproximar a la distribución normal la distribución resultante de aplicar estadísticas (ej., promedios, varianza) a muestras. La distribución t es bastante robuzta, incluso en situaciones donde el tamaño de la muestra es pequeño

<img class=center src="../assets/img/t-distribution.png" height=300 />

---

## T-test en R

* En R la función para realizar un análisis de t-test es ```t.test```

* Ejemplo. Diferencia en los meses de estudio entre los que becarios de la capital y el resto 
  * **H0**: No existe diferencia en los meses de estudio entre los becarios de la capital y el resto
  * **HA**: Existe diferencia en los meses de estudio entre los becarios de la capital y el resto




```r
t.test(estudios_capital, estudios_resto, alternative = "two.sided")
```

```
## 
## 	Welch Two Sample t-test
## 
## data:  estudios_capital and estudios_resto
## t = 4.9992, df = 555.95, p-value = 7.728e-07
## alternative hypothesis: true difference in means is not equal to 0
## 95 percent confidence interval:
##  2.222666 5.099731
## sample estimates:
## mean of x mean of y 
##  18.71714  15.05594
```

---

## ANOVA

* T-test es muy útil para comparar 2 grupos de datos, pero, ¿qué pasaría si tuvieramos que **comparar más de 2 grupos**?

* En caso de tener más de 2 grupos, el procedimiento estadístico que se utiliza para comprobar la significancia estadística en la diferencia entre estos se llama **Análisis de Varianza** o **ANOVA**

* ANOVA está basado en la prueba **estadística F** la cual mide la proporción de la varianza entre los grupos y la varianza intra grupos. 

* Si el resultado de la estadística F es menor a 1 (la varianza intra grupos es mayor a la entre grupos) no existe diferencia entre los grupos

* Mientras, que si el resultado de la estadística F es mayor a 1 (la varianza entre grupos es mayor a la varianza intra grupos) existe diferencia entre los grupos

---

## ANOVA en R

* En R la función para realizar un análisis ANOVA es ```aov```

* Ejemplo. Diferencia en meses de estudio entre los de capital, central, e interior del país
  * H0: No existe diferencia en meses de estudio entre los becarios residentes en capital, central, e interior del país
  * HA: Existe diferencia en meses de estudio entre los becarios residentes en capital, central, e interior del país




```r
summary(aov(meses_estudio ~ localidad, data=aov_estudios))
```

```
##              Df Sum Sq Mean Sq F value   Pr(>F)    
## localidad     2   3341  1670.7    20.8 1.55e-09 ***
## Residuals   801  64325    80.3                     
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```

---

## Chi-square Test

* Hasta el momento vimos como estudiar relaciones entre variables categóricas (ej., lugar de residencia) y variables discretas (ej., meses de estudio), pero como haríamos si quisieramos evaluar la relación de dos variables categóricas (ej., sexo y lugar de residencia)?

* Para el análisis de variables categóricas se utiliza el **test chi-squared** que evalua si las variables de interés son independientes unas de otra

* Chi-square se basa en comparar el número de valores observados (los datos) contra el número de valores esperados asumiendo que las variables son independientes

--- &twocol

## Chi-square Test

* Ejemplo. Relación entre sexo de becarios y categoría de universidad (top 10, top 50, etc.)
  * H0: Existe igual cantidad de becarios y becarias en las universidades top 10 y top 50
  * HA: El número de mujeres y hombres en las universidades top 10 y top 50 es diferente

*** =left

* Valores observados

Tipo Univ/Sexo | top 10 | top 50 | Total
-------------- | ------ | ------ | -----
Femenino       |  12    |  56    | 68
Masculino      |  5     |  39    | 44
Total          |  17    |  95    | 112

*** =right

* Valores esperados

Tipo Univ/Sexo | top 10 | top 50 | Total
-------------- | ------ | ------ | -----
Femenino       |  10    |   58   | 68  (0,6)
Masculino      |  7     |   37   | 44  (0,4)
Total          |  17    |   95   | 112 (1,0)

--- 

## Chi-square en R



En R el test chi-square se realiza por medio de la función ```chisq.test```


```r
chisq.test(table(becarios_top_50$sexo,droplevels(becarios_top_50$categoriauni)))
```

```
## 
## 	Pearson's Chi-squared test with Yates' continuity correction
## 
## data:  table(becarios_top_50$sexo, droplevels(becarios_top_50$categoriauni))
## X-squared = 0.40386, df = 1, p-value = 0.5251
```

---

## Tests y tipos de variables

Dependiente/Independiente | Categórica | Ordinal    | Discreta     | Continua
--------------------------|------------|------------|--------------|---------
Categórica                | Chi-square | Chi-square | T-test/ANOVA | T-test/ANOVA
Ordinal                   | Chi-square | Chi-square |              |
Discreta                  |            |            | Correlación  |
Continua                  |            |            |              | Correlación
