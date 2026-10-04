# Control de Levitación Neumática

Sistema de levitación neumática desarrollado para controlar la altura de una pelota dentro de un tubo mediante flujo de aire.

El proyecto integra identificación de sistemas, modelado dinámico, control PID digital, simulación en MATLAB/Simulink e implementación experimental utilizando un ESP32.

## Tecnologías utilizadas

- ESP32
- MATLAB
- Simulink
- Control PID digital
- Identificación de sistemas
- Sensor VL53L0X
- PWM
- Driver L298N
- Impresión 3D
- Arduino

## Sistema

La planta está compuesta por:

- Tubo vertical de 70 cm
- Pelota de ping-pong
- Ventilador DC de 24 V
- Driver L298N
- Sensor de distancia VL53L0X
- ESP32

El objetivo es mantener la pelota en una altura de referencia regulando la velocidad del ventilador mediante PWM.

Flujo general:

`Referencia → PID → PWM → Ventilador → Pelota → Sensor VL53L0X → ESP32`

## Identificación de la planta

El comportamiento dinámico del sistema fue identificado experimentalmente aplicando una señal escalón al ventilador y registrando la posición de la pelota.

Los datos obtenidos fueron procesados mediante MATLAB utilizando herramientas de identificación de sistemas.

Se utilizó un modelo P3I para estimar los parámetros principales de la planta.

## Control PID

El controlador fue diseñado inicialmente utilizando el método de Ziegler-Nichols.

Durante las pruebas experimentales se realizaron ajustes adicionales para mejorar la estabilidad del sistema.

El controlador se implementó en tiempo discreto con un período de muestreo de:

`Ts = 20 ms`

## Anti-Windup

Se implementó un mecanismo de anti-windup mediante integración condicional.

Esta estrategia evita que el término integral continúe acumulándose cuando el actuador se encuentra saturado, reduciendo sobreimpulsos y mejorando la estabilidad del sistema.

## Simulación

El sistema fue modelado y simulado en MATLAB/Simulink antes de su implementación física.

El modelo incluye:

- Planta identificada
- Controlador PID digital
- Dinámica del sensor
- Señales de referencia
- Visualización de la respuesta

## Implementación experimental

El controlador fue implementado en un ESP32.

El sistema permite modificar mediante comunicación serial:

- Kp
- Ki
- Kd
- Referencia de altura
- Tiempo de muestreo
- Parámetros de filtrado

También se visualizan en tiempo real variables como:

- Altura
- Error
- Salida PID
- PWM

## Resultados

Las pruebas experimentales mostraron que el sistema puede seguir referencias de altura de manera estable.

La incorporación del esquema anti-windup permitió obtener una llegada a la referencia más progresiva y reducir los efectos de saturación del actuador.

## Archivos

Código del ESP32:

`esp32/main.ino`


## Documentación

El informe completo del proyecto está disponible aquí:

[Ver informe del proyecto](docs/Project_Report.pdf)

## Autores

- Victor Curiel
- Ximena Quenhan

Universidad Nacional de Asunción  
Facultad de Ingeniería  
Ingeniería Mecatrónica

## Licencia

Este proyecto está distribuido bajo la licencia MIT.
