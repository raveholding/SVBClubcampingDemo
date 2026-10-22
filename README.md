# Sistema VB · Demo de gestión de clubes de camping

Demo funcional e interactiva de un sistema integral para clubes de camping: predio, reservas y estadías, gastronomía, cargos cruzados, subalquileres y contabilidad. Todo corre en el navegador desde un único archivo `index.html`, sin backend ni instalación. **Todos los datos son ficticios.**

## Cómo usarla

1. Descargá `index.html` (o cloná el repo).
2. Abrilo con doble clic en Chrome, Edge, Firefox o Safari actualizados.
3. La demo arranca con datos precargados y fechas relativas al día de hoy.
4. Para volver al estado inicial: **Configuración y pruebas → Datos de la demo → Restablecer datos de demostración**.

Los cambios se guardan en `localStorage`. Si el navegador lo bloquea (por ejemplo, en modo privado), la app sigue funcionando en memoria y lo avisa con un banner.

## Recorrido sugerido

1. **Mapa del predio** → tocá **P04** (libre) → *Check-in rápido* → elegí un socio, fechas, personas y vehículos. El precio se calcula en vivo (base, adicionales, temporada alta, descuento de socio).
2. **Mapa gastronómico** → tocá una mesa libre → *Abrir cuenta* asociada a P04 → agregá 2 cervezas y 1 hamburguesa → *Imputar consumo a parcela*.
3. **Mapa del predio** → P04 → **Ejecutar Check-Out y Cierre de Estancia** → revisá cargos, pagos, saldo y asiento previsto → confirmá → comprobante.
4. Mirá cómo cambian el **Dashboard**, **Caja y contabilidad** (libro diario y controles de integridad) y **Reportes**.
5. Probá P02: su check-out queda bloqueado porque tiene un ticket abierto en BAR-M02.
6. **Configuración y pruebas → Pruebas funcionales** ejecuta las 15 pruebas obligatorias sobre una copia aislada de los datos.

## Módulos

Dashboard · Socios y clientes · Mapa del predio (SVG) · Reservas y estadías · Mapa gastronómico (14 unidades) · Consumos y cuentas (tickets, cargos cruzados, pagos directos, inventario) · Subalquileres y propietarios (liquidación 70/30 configurable) · Caja y contabilidad (libro diario, sumas y saldos, tesorería, política contable) · Reportes · Configuración (tarifas, temporada alta, datos, pruebas).

## Reglas destacadas

- Importes en centavos enteros y una única función de cálculo (`calcularAlojamiento`).
- Descuento de socio solo con condición de socio activo **y** cuotas al día; se aplica una vez.
- Temporada alta por noche, solo sobre la tarifa base (configurable).
- Sin superposición de reservas ni check-in en unidades en mantenimiento.
- El stock se descuenta una sola vez al cerrar el ticket; el precio queda fijado en cada línea.
- Operaciones atómicas e idempotentes: check-out, imputaciones y liquidaciones no se duplican.
- Asientos validados (Debe = Haber) antes de guardarse. Política de reconocimiento bruto con reclasificación de la parte del propietario.

## Limitaciones conocidas

Es un prototipo para validar flujos. Los datos viven solo en el navegador; no hay usuarios, permisos, auditoría persistente, integración con medios de pago ni facturación electrónica. La contabilidad es una simulación: no es un sistema contable certificado ni garantiza el cumplimiento de normas fiscales argentinas. Una versión productiva requiere backend, base de datos, autenticación y validación contable/fiscal.
