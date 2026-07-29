# Tu Essence

Sitio estático mobile-first para el catálogo local de perfumes de Tu Essence en Connecticut. Está construido con Astro y TypeScript y usa JavaScript mínimo para filtrar productos. No incluye carrito, pagos, cuentas ni base de datos.

> **Importante:** el catálogo usa las 27 imágenes actuales de `public/images/perfumes/`. Los precios finales están registrados en `src/data/perfumes.ts`; MURJAN W muestra una promoción especial pendiente de precio.

## Requisitos

- Node.js 24 LTS
- npm 11 o compatible

## Desarrollo

```bash
npm install
npm run dev
```

Astro mostrará la URL local en la terminal. Para comprobar tipos y generar la versión de producción:

```bash
npm run check
npm run build
```

La carpeta generada para Netlify es **`dist`**. `netlify.toml` ya usa `npm run build` como comando y `dist` como directorio de publicación.

## Cambiar productos, precios y frases

Todos los productos viven en un único archivo:

```text
src/data/perfumes.ts
```

Cada registro usa estos campos:

| Campo | Uso |
| --- | --- |
| `id` | Identificador único, sin espacios |
| `nombre` | Nombre visible y texto del mensaje de WhatsApp |
| `precio` | Precio visible y texto del mensaje de WhatsApp |
| `categoria` | Solo `"hombre"`, `"mujer"` o `"unisex"` |
| `frase` | Descripción corta de la tarjeta |
| `imagen` | Ruta local que comienza con `/images/perfumes/` |
| `disponible` | `true` o `false` |

Los contadores del catálogo se calculan automáticamente desde los registros; no requieren cambios manuales.

El mensaje de cada botón se genera automáticamente con este formato:

```text
Hola Tu Essence, me interesa [nombre] por [precio]. ¿Está disponible?
```

## Fotografías del catálogo

Guarda las fotografías en:

```text
public/images/perfumes/
```

Cada imagen actual tiene un registro correspondiente en `src/data/perfumes.ts`:

```text
AL NOBLE.png
ALMAS NOVELTY.png
AZZARO BY NIGHT.png
AZZARO THE MOST WANTED.png
GLAIER GOLD.jpeg
HAWAS ICE.png
HER CONFESSION.png
HIS CONFESSION.png
ICONIC.png
ITALIA.png
LIONHEART WOMEN.png
MAHD DORADO.png
MALEKA.png
MURJAN W.png
NITRO RED.png
NITRO WHITE.png
ODYSSEY SKY MANDARIN.png
ROME IMAGINE.png
RUBY BAHIYA.png
SOPRANO ICE.png
STRONGER WY INTENSELY.png
SUPREMACY COLLECTOR.jpeg
UHUD.png
VENENO.png
VULCAN FEU.png
WORLD CUP VIP.png
YARA ELIXIR.png
```

Recomendaciones para cada foto:

- Formato WebP.
- Proporción vertical `4:5`.
- Tamaño aproximado de `800 × 1000 px`.
- Fondo limpio y encuadre consistente.
- Peso ideal inferior a 150 KB.

Si una foto no existe o falla, la tarjeta cambia automáticamente a `public/images/placeholder-perfume.svg`.

## Contacto

Los enlaces confirmados están definidos en `src/pages/index.astro`:

- WhatsApp Business: `https://wa.me/12039087955`
- Instagram directo: `https://ig.me/m/tuesencia_usa`
- Perfil alternativo: `https://www.instagram.com/tuesencia_usa/`

## SEO y publicación

- El título, la descripción, la URL canónica y Open Graph están en `src/layouts/Layout.astro`.
- La URL base y el sitemap están configurados en `astro.config.mjs`.
- `public/robots.txt` referencia el sitemap.
- `public/manifest.webmanifest` y `public/favicon.svg` cubren la identidad básica del navegador.
- `public/og.png` es la vista previa local para compartir.

Si cambia el dominio final, actualiza `site` en `astro.config.mjs` y la URL del sitemap en `public/robots.txt`.

En Netlify, conecta el repositorio o sube el proyecto. La configuración de compilación se detectará desde `netlify.toml`.
