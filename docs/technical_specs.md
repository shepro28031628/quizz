# Especificaciones Técnicas - Quiz AgroTech

## Estructura del Proyecto
- `index.html`: Aplicación principal (HTML5/JS/Tailwind).
- `/assets`: Repositorio de 13 imágenes temáticas vinculadas por rutas relativas.
- `/docs`: Documentación técnica.

## Lógica de Funcionamiento
El sistema utiliza un motor de cuestionario en JavaScript Vanilla que gestiona un array de objetos `questions`.

### Componentes Clave:
- **Dinamismo**: El contador (`question-counter`) y la barra de progreso (`progress-bar`) se calculan en tiempo real basándose en la longitud del array `questions.length`.
- **Estilos**: Se utiliza **Tailwind CSS** para el diseño responsivo y **CSS puro** para efectos avanzados como el gradiente radial del fondo y el efecto de vidrio (*Glassmorphism*).
- **Multimedia**: Las imágenes se cargan de forma diferida (`onload`) para asegurar una transición suave con animaciones de opacidad.

## Mantenimiento y Escalabilidad
Para añadir nuevas preguntas al sistema:
1. Localizar el array `const questions` en el bloque de `<script>`.
2. Insertar un nuevo objeto con la estructura:
   ```javascript
   {
       question: "Texto de la pregunta",
       image: "assets/nueva_imagen.png",
       options: [
           { text: "Opción A", isCorrect: false, rationale: "Explicación" },
           { text: "Opción B", isCorrect: true, rationale: "Explicación" }
       ]
   }
   ```
3. El sistema recalibrará automáticamente el progreso del 0% al 100%.

## Flujo de Estados
```text
[Inicio] -> [Carga Pregunta i] -> [Selección de Opción]
                                    |
            [Feedback Visual (Correcto/Incorrecto)]
                                    |
            [Explicación Técnica (Rationale)]
                                    |
            [¿Es la última?] --No--> [Siguiente Pregunta (i++)]
                 |
                Si
                 |
            [Cálculo de Score Final] -> [Pantalla de Resultados]
```
