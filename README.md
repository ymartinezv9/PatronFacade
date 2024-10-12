# PatronFacade

# Índice

1. [¿Qué es el patrón Facade?](#1-¿qué-es-el-patrón-facade)
2. [Ventajas del patrón Facade](#2-ventajas-del-patrón-facade)
3. [Ejemplo del Patrón Facade: Sistema de Inscripción de Estudiantes UMG](#3-ejemplo-del-patrón-facade-sistema-de-inscripción-de-estudiantes-umg)
   - [Código en Java](#código-en-java)
   - [Resultado en consola](#resultado-en-consola)
4. [Explicación](#explicación)
5. [Conclusión](#conclusión)

---

# Índice

1. [¿Qué es el patrón Facade?](#1-¿qué-es-el-patrón-facade)
2. [Ventajas del patrón Facade](#2-ventajas-del-patrón-facade)
3. [Ejemplo del Patrón Facade: Sistema de Inscripción de Estudiantes UMG](#3-ejemplo-del-patrón-facade-sistema-de-inscripción-de-estudiantes-umg)
   - [Código en Java](#código-en-java)
   - [Resultado en consola](#resultado-en-consola)
4. [Explicación](#explicación)
5. [Conclusión](#conclusión)

---

## 1. ¿Qué es el patrón Facade?

El patrón **Facade** es un patrón de diseño estructural que proporciona una interfaz simplificada para un conjunto de clases más complejas o subsistemas. Su objetivo principal es ocultar la complejidad de las interacciones entre múltiples clases y ofrecer una interfaz más amigable al cliente que lo utiliza.

Este patrón es útil cuando se interactúa con sistemas complejos y se desea evitar que los clientes tengan que entender o gestionar todos los detalles internos. El **Facade** actúa como un punto de acceso único a toda la funcionalidad subyacente.

## 2. Ventajas del patrón Facade

- **Simplificación**: Ofrece una interfaz simple y comprensible para interactuar con un sistema complejo.
- **Desacoplamiento**: Reduce la dependencia del cliente sobre las clases internas del sistema.
- **Mantenimiento**: Hace que el código sea más fácil de mantener, ya que los cambios en el sistema complejo no afectan directamente a los clientes que usan el **Facade**.
- **Centralización**: Unifica la lógica de acceso y oculta los detalles de implementación detrás de una interfaz más sencilla.

## 3. Ejemplo del Patrón Facade: Sistema de Inscripción de Estudiantes UMG

En este ejemplo, queremos desarrollar un sistema de inscripción para los estudiantes de la UMG. El sistema interactúa con varios subsistemas, como la matrícula, la base de datos de estudiantes, y la gestión de pagos. Para facilitar su uso, creamos un **Facade** que simplifica todas estas interacciones.

### Código en Java

```java
// Subsistema 1: Matricula
class Matricula {
    public void registrarEstudiante(String nombre) {
        System.out.println("Registrando al estudiante: " + nombre);
    }
}

// Subsistema 2: Base de datos de estudiantes
class BaseDatosEstudiantes {
    public void guardarEstudiante(String nombre) {
        System.out.println("Guardando al estudiante " + nombre + " en la base de datos.");
    }
}

// Subsistema 3: Gestión de pagos
class GestionPagos {
    public void procesarPago(String nombre) {
        System.out.println("Procesando pago de matrícula para: " + nombre);
    }
}

// Facade: Sistema de Inscripción
class SistemaInscripcionFacade {
    private Matricula matricula;
    private BaseDatosEstudiantes baseDatos;
    private GestionPagos gestionPagos;

    public SistemaInscripcionFacade() {
        matricula = new Matricula();
        baseDatos = new BaseDatosEstudiantes();
        gestionPagos = new GestionPagos();
    }

    public void inscribirEstudiante(String nombre) {
        matricula.registrarEstudiante(nombre);
        baseDatos.guardarEstudiante(nombre);
        gestionPagos.procesarPago(nombre);
        System.out.println("Inscripción completa para: " + nombre);
    }
}

// Uso del patrón Facade
public class Main {
    public static void main(String[] args) {
        SistemaInscripcionFacade sistemaInscripcion = new SistemaInscripcionFacade();
        sistemaInscripcion.inscribirEstudiante("Juan Pérez");
    }
}
```
### Resultado en consola

```bash
Registrando al estudiante: Juan Pérez
Guardando al estudiante Juan Pérez en la base de datos.
Procesando pago de matrícula para: Juan Pérez
Inscripción completa para: Juan Pérez
```
## 4. Explicación

- **Matricula**: Subsistema encargado de registrar al estudiante.
- **BaseDatosEstudiantes**: Subsistema que gestiona la base de datos de los estudiantes.
- **GestionPagos**: Subsistema que se encarga de procesar los pagos de matrícula.
- **SistemaInscripcionFacade**: Es el **Facade** que oculta la complejidad de interactuar con los tres subsistemas. Desde su método `inscribirEstudiante`, se llama a las funcionalidades necesarias de los subsistemas para completar el proceso de inscripción.

El cliente, en este caso, solo necesita interactuar con el `SistemaInscripcionFacade` y no con cada subsistema individualmente, lo que simplifica el uso del sistema.

## 5. Conclusión

El patrón **Facade** es una excelente solución cuando se trata de sistemas complejos con múltiples subsistemas. Facilita la interacción al proporcionar una interfaz simple y clara, mientras que mantiene la funcionalidad completa disponible. En el caso del sistema de inscripción de estudiantes de la UMG, el **Facade** nos permitió centralizar y simplificar el proceso de registro, almacenamiento y pago de la matrícula, evitando que el cliente tenga que interactuar directamente con cada subsistema.

