# MANA

Juego de construcción de mazo para 2–4 jugadores (30–55 min). Cada jugador es un Guardián que
vincula Elementales de Fuego, Agua, Tierra y Aire y pone Presencia en cuatro Santuarios. Tras tres
Eras gana quien reúna más Sellos. Reglas: [REGLAS.md](REGLAS.md).

## Jugar con amigos (Render)

El repositorio incluye `render.yaml`, así que Render lo configura solo:

1. Entra en <https://dashboard.render.com> (con tu cuenta de GitHub).
2. **New → Blueprint**.
3. Elige el repositorio **polupon-coder/mana** (si no aparece: *Configure account* y dale acceso).
4. Render lee `render.yaml` y muestra el servicio `mana` (plan Free). Pulsa **Apply** / **Deploy Blueprint**.
5. Espera 2–3 minutos a que ponga **Live** y abre la dirección, del estilo `https://mana-xxxx.onrender.com`.

Cada vez que se suben cambios a `main`, Render vuelve a publicar el juego solo.

Para jugar: pon tu nombre, **Con amigos → Crear partida**, pulsa **Copiar** y pasa el enlace. Tus
amigos lo abren, ponen su nombre y pulsan **Unirme**. Los huecos libres los juegan bots.

> Plan gratuito: el servidor se duerme tras ~15 minutos sin uso y tarda 30–60 s en despertar
> (ábrelo un minuto antes de quedar). Las partidas se guardan en memoria: si el servidor se
> reinicia, la partida en curso se pierde. Los bots los mueve la pantalla de quien creó la partida.

## Archivos

| Archivo | Qué es |
| --- | --- |
| `cartas.js`, `motor.js` | Cartas y motor de reglas, con los bots. |
| `web/jugar.html` | La mesa (plantilla); `web/construir.js` la empaqueta con todo dentro en `jugar.html`. |
| `web/elementales/`, `web/texturas/` | Ilustraciones, texturas y letra. |
| `servidor/servidor.js` | Servidor sin dependencias: sirve `jugar.html` y reparte la partida entre jugadores. |
| `simular.js`, `valor_cartas.js`, `afinidad.js`, `duracion.js` | Simulaciones para equilibrar el juego ([EVALUACION.md](EVALUACION.md)). |
| `maqueta/` | Maquetas de diseño. |

## Desarrollo

```
npm test             # pruebas
npm run construir    # vuelve a generar jugar.html tras tocar web/jugar.html, cartas o motor
npm start            # servidor en http://localhost:3000
```
