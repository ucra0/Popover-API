# Investigación: Popover API (HTML & CSS)

Este repositorio contiene un ejemplo práctico sobre la **Popover API**, una novedad técnica introducida recientemente en los estándares web para gestionar elementos superpuestos (tooltips, menús, notificaciones) de forma nativa.

## 🎯 Objetivo de la Práctica
Demostrar cómo la Popover API simplifica la creación de interfaces de usuario complejas, eliminando la dependencia de librerías externas o hacks de CSS (`z-index`) y mejorando la accesibilidad por defecto.

## 📚 Teoría de la Novedad

### ¿Qué es?
La Popover API permite definir elementos que se muestran en la **Top Layer** (capa superior) del navegador. Esto significa que el elemento "flota" por encima de todo el resto del documento, sin importar dónde esté escrito en el HTML y sin verse afectado por `overflow: hidden` o contextos de apilamiento (stacking contexts) de sus padres.

### Evolución Técnica
| Método Anterior | Popover API |
| :--- | :--- |
| **`z-index: 9999`**: Difícil de gestionar, conflictos constantes. | **Top Layer**: El navegador gestiona la superposición automáticamente. |
| **JavaScript Listeners**: Necesario para detectar clics fuera (`document.addEventListener`). | **Light Dismiss**: Comportamiento nativo con `popover="auto"`. |
| **Posicionamiento**: Necesidad de mover el HTML al final del `<body>`. | **Flexible**: El código puede estar anidado profundamente, pero se renderiza arriba. |

## 🛠 Implementación y Sintaxis

El proyecto implementa dos variantes clave:

### 1. Popover Automático (`popover="auto"`)
Utilizado en el **Menú de Usuario**.
- **Comportamiento:** Solo un popover de este tipo puede estar abierto a la vez.
- **Cierre:** Se cierra automáticamente al hacer clic fuera (Light Dismiss) o pulsar `Esc`.
- **Código:**
  ```html
  <button popovertarget="mi-menu">Abrir</button>
  <div id="mi-menu" popover="auto">Contenido</div>
  ```

### 2. Popover Manual (`popover="manual"`)
Utilizado en el **Panel de Notificaciones**.
- **Comportamiento:** Puede convivir con otros popovers abiertos. No bloquea la interacción con el resto de la página.
- **Cierre:** Requiere una acción explícita (botón de cerrar).
- **Código:**
  ```html
  <div id="aviso" popover="manual">
      <button popovertarget="aviso" popovertargetaction="hide">X</button>
  </div>
  ```

## 🚀 Cómo probar el ejemplo
1. Clona el repositorio.
2. Abre `index.html` en un navegador moderno (Chrome 114+, Edge 114+, Safari 17+, Firefox 125+).
3. Interactúa con el botón "Perfil" para ver el *Light Dismiss*.
4. Abre "Alertas" para ver un elemento persistente que no bloquea la página.
