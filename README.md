# Notas visuales — Capítulo Ecuador

Maqueta web del fotolibro de Pedro Luis González. Construida en HTML/CSS/JS
autocontenido, sin dependencias externas más allá de Google Fonts.

## Estructura

```
notas-visuales/
├── index.html          ← todo el sitio (estructura + estilos + lógica)
├── images/              ← las 80 fotografías + portada/contraportada
└── README.md
```

## Estado actual

- **40 dípticos completos**, extraídos del PDF `dipticos.pdf` con la
  nomenclatura `NN-A.jpg` / `NN-B.jpg` (excepción: `11-A.jpg` / `11-BC.jpg`,
  donde `11-BC` es el compuesto de las dos fotos que van en la página derecha
  de ese díptico).
- **Páginas cuadradas**: cada foto se ajusta dentro de un marco cuadrado sin
  recortarse (`object-fit: contain`), para que las fotos verticales (2:3) y
  horizontales (3:2) ocupen el mismo espacio de página.
- **Portada y contraportada**: aún son placeholders (recuadros numerados).
  Cuando Pedro elija las imágenes finales, deben guardarse como:
  - `images/00-portada.jpg`
  - `images/99-contraportada.jpg`
- **Nota del autor**: texto placeholder marcado explícitamente como borrador
  dentro del propio sitio. Falta la versión final de Pedro.
- **Contacto**: correo e Instagram son de ejemplo — reemplazar en el bloque
  `<section class="contacto">` de `index.html`.

## Cómo reemplazar una foto

Cada imagen se referencia por nombre de archivo dentro de `images/`. Basta
con sobrescribir el archivo correspondiente (mismo nombre) o, si cambias de
nombre, actualizar el arreglo `diptychs` al final de `index.html`.

## Cómo cambiar el orden de los dípticos

El orden de aparición está controlado por el arreglo `diptychs` generado en
el `<script>` al final de `index.html`. Para reordenar, construye el arreglo
a mano en vez del bucle automático, por ejemplo:

```js
const diptychs = [
  { folio: 1, left: '01-A.jpg', right: '01-B.jpg' },
  { folio: 2, left: '05-A.jpg', right: '05-B.jpg' }, // ejemplo de swap
  // ...
];
```

El número de `folio` que se muestra en pantalla es independiente del nombre
de archivo, así que puedes reordenar sin renombrar imágenes.

## Publicar en GitHub Pages

1. Crea un repositorio nuevo (o usa uno existente) y sube el contenido de
   esta carpeta (`index.html`, `images/`, este `README.md`) a la raíz del
   repositorio, o a una carpeta `/docs` si prefieres mantenerlo separado.
2. En GitHub: **Settings → Pages → Source**, selecciona la rama y carpeta
   donde subiste los archivos.
3. GitHub publicará el sitio en `https://<usuario>.github.io/<repositorio>/`
   en unos minutos.
4. Cada vez que reemplaces fotos o edites `index.html`, solo necesitas subir
   (`git push`) los cambios — no hace falta rehacer nada más.
