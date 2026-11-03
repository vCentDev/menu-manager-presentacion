# MenuManager · Carta digital bilingüe para un restaurante

Los comensales pueden buscar platos en español o inglés, consultar precios y excluir los que contienen los alérgenos que seleccionen. El personal autorizado puede actualizar precios y disponibilidad desde un panel de administración.

Desarrollo íntegramente realizado por [Vicente Marco](https://github.com/vCentDev) para un cliente. El proyecto está **en desarrollo y pendiente de entrega**; aún no hay una URL de producción. El código fuente se mantiene en un repositorio privado y este repositorio muestra la interfaz mediante capturas y vídeos.

## Vista rápida

Carta en escritorio: búsqueda, selección de alérgenos, cambio de idioma y navegación entre secciones.

![Carta de MenuManager en escritorio y en inglés, con búsqueda, filtro de alérgenos y platos con precios y descripciones](imagenes/menu-manager-carta.png)

## Ver el proyecto en funcionamiento

- **[Carta pública: exploración del menú](https://github.com/user-attachments/assets/ab177397-51f7-490f-87f9-3db7471c0916)** — vídeo de la experiencia de consulta para comensales.
- **[Inicio de sesión y panel de administración](https://github.com/user-attachments/assets/45ecbaa0-ee11-4daf-b2b7-b2360e13a22b)** — vídeo del acceso y la vista de gestión.

## Alcance implementado

**Carta pública**

- Platos disponibles agrupados en secciones, con navegación por anclas y búsqueda por nombre o descripción sin distinguir mayúsculas ni tildes.
- Exclusión de platos que contienen cualquiera de los alérgenos seleccionados.
- Interfaz y contenido en español e inglés, con preferencia de idioma guardada en el navegador y uso de la otra traducción cuando falta la solicitada.
- Estados de carga, error con reintento y ausencia de resultados.

**Administración**

- Inicio y cierre de sesión mediante Supabase Auth, con comprobación de sesión y rol antes de acceder al panel.
- Búsqueda, filtros y ordenación de platos; edición de precios y disponibilidad con recuperación del valor anterior si falla el guardado.
- Avisos de error de guardado y de traducciones ES/EN ausentes.

## Cómo está construido

- **Estado e idiomas.** Angular Signals y `computed` mantienen los filtros y los platos visibles; ngx-translate gestiona los textos de la interfaz y Supabase almacena las traducciones del contenido.
- **Datos y acceso.** Clientes y mapeadores separan las respuestas de Supabase de los modelos de la aplicación. Los guards comprueban sesión y rol para acceder al panel; la protección de los datos depende además de los permisos de la base de datos.
- **Edición optimista.** El panel muestra el nuevo precio o disponibilidad mientras guarda. Si falla la escritura, restaura el valor anterior y muestra un aviso. Los precios se almacenan en céntimos.

## Tecnologías

- Angular 21, TypeScript, PrimeNG y PrimeUIX Themes.
- Supabase para datos y autenticación; ngx-translate para la interfaz bilingüe.
- CSS con variables compartidas y estilos adaptables a móvil y escritorio.

## Estado y próximos pasos

La consulta de la carta y la actualización de precios y disponibilidad están implementadas. Quedan pendientes el alta, la edición completa y el borrado de platos, así como la gestión de traducciones, alérgenos y secciones desde el panel. La pestaña Secciones todavía muestra un mensaje provisional.

También faltan migraciones y datos iniciales para reproducir la base de datos, pruebas automatizadas de los recorridos críticos e integración continua.

## Recursos utilizados

Créditos visuales: componentes de PrimeNG, preset basado en Aura de PrimeUIX Themes y fuentes DM Sans, Playfair Display y DM Mono.
