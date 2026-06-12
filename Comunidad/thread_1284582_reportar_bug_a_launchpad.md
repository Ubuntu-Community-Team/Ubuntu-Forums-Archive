---
title: "reportar bug a launchpad"
date: 2009-10-06
forum: Comunidad
---

### Post by z37a on 2009-10-06
Gente, una consulta, quiero reportar un bug a lounchpad, pero no encuentro como, veran el problema es antes del booteo y no saleobviamente ninguna pantalla de reportar bug, desde el sitio me fije un poco que onda peor no encuentro el como reportar un bug en forma manual, alguno podra decirme si se puede, como hacerlo?

---

### Post by pablo.s on 2009-10-06
> **z37a said:**
> Gente, una consulta, quiero reportar un bug a lounchpad, pero no encuentro como, veran el problema es antes del booteo y no saleobviamente ninguna pantalla de reportar bug, 

¿Podés especificar cuál es 
el problema? Es probable que
no tengas que reportar un bug
a Launchpad sino a otro lado.


> **z37a said:**
> desde el sitio me fije un poco que onda peor no encuentro el como reportar un bug en forma manual, alguno podra decirme si se puede, como hacerlo?

Desde Ubuntu hay una herramienta
que se llama apport diseñada para el
reporte de bugs. Te pide un PID ( que es
el identificador del proceso) para asignar
el bug al programa en cuestión.

---

### Post by juancarlospaco on 2009-10-06
Ver las cosas que hay que tener antes de reportar un Bug,
*ejemplos al azar: todos los updates, que el Bug ya este reportado, etc*

---

### Post by santiagoward2000 on 2009-10-06
> **z37a said:**
> Gente, una consulta, quiero reportar un bug a lounchpad, pero no encuentro como, veran el problema es antes del booteo y no saleobviamente ninguna pantalla de reportar bug, desde el sitio me fije un poco que onda peor no encuentro el como reportar un bug en forma manual, alguno podra decirme si se puede, como hacerlo?

Si querés hacerlo desde el sitio de Launchpad, tenés que ir a la página del proyecto que querés reportar el bug (supongo que en este caso, al ser un problema antes de bootear deberías reportarlo a Ubuntu), ir a la pestaña **Bugs** y ahí elegir **Report a bug** (arriba a la derecha).
Saludos!

---

### Post by z37a on 2009-10-06
El bug, y creo que es un bug(100% seguro) es con respecto a Karmic, el live del beta en versión 64 bits no inicia de ninguna forma en una pc con un Turion64 Compaq CQ50, algo del hardware no es compatible, la imagen del bootcd queda colgada en "Probar Ubuntu sin..." o en "Instalar..." el Memtest Funciona de 10. Sinembargo en la misma PC la version i586 funciona perfectamente, obviamente en caso de reportarlo como tal pasaria un lspci y algun que otro detalle para ver bien el hard, pero ahy un problema de compatibilidad según vi.

Otro dato, si fuese que la PC no es de 64 bits(cosa muy dificil de creer siendo un Turion64 x2) deberia dar el clasico mensaje de que no es una arquitectura compatible, pero ni eso.

---

### Post by guillermolisi on 2009-10-06
> **santiagoward2000 said:**
> Si querés hacerlo desde el sitio de Launchpad, tenés que ir a la página del proyecto que querés reportar el bug (supongo que en este caso, al ser un problema antes de bootear deberías reportarlo a Ubuntu), ir a la pestaña **Bugs** y ahí elegir **Report a bug** (arriba a la derecha).
Saludos!
Si señor. Primero se reporta a Ubuntu y luego ellos lo derivan a quien corresponda o te piden que lo informes en otro lado, si el tema los supera.

---

### Post by pablo.s on 2009-10-06
> **z37a said:**
>  la imagen del bootcd queda colgada en "Probar Ubuntu sin..." o en "Instalar..." el Memtest Funciona de 10. Sinembargo en la misma PC la version i586 funciona perfectamente, obviamente en caso de reportarlo como tal pasaria un lspci y algun que otro detalle para ver bien el hard, pero ahy un problema de compatibilidad según vi.

Factores a analizar:

1) La imagen del cd de 64bits está
chequeada para ver si ha sido
grabada de forma correcta?
Podés hacer MD5sum para que
verifique si la .iso está íntegra?

2) Si se cuelga en ese punto, podés
pasar a la primera consola con la
combinación CTRL+Alt+F1 y ver si
hay algún mensaje o linea de error.

3) Con la versión Alternate hace lo
mismo?

Son pequeños detalles que consideraría
antes de reportar un bug. En caso de
que lo reportes, esta información sería
de gran utilidad al equipo de pruebas.

---

### Post by guillermolisi on 2009-10-06
> **pablo.s said:**
> ¿Podés especificar cuál es 
el problema? Es probable que
no tengas que reportar un bug
a Launchpad sino a otro lado.

Desde Ubuntu hay una herramienta
que se llama apport diseñada para el
reporte de bugs. Te pide un PID ( que es
el identificador del proceso) para asignar
el bug al programa en cuestión.
Apport genera toda la bateria de archivos necesarios para analizar el problema, conocer las caracteristicas de la maquina y el contexto dentro del cual ocurrio el supuesto incidente. De hecho cuando posteas tu primer comentario, si le ven consistencia al problema, lo primero que te piden es que actives la herramienta (que me parece necesita tu certificacion digital de Launchpad o al menos user & pass) y se genera otro post con toda la informacion (archivos).

---

### Post by pablo.s on 2009-10-06
> **guillermolisi said:**
> Apport genera toda la bateria de archivos necesarios para analizar el problema, conocer las caracteristicas de la maquina y el contexto dentro del cual ocurrio el supuesto incidente. De hecho cuando posteas tu primer comentario, si le ven consistencia al problema, lo primero que te piden es que actives la herramienta (que me parece necesita tu certificacion digital de Launchpad o al menos user & pass) y se genera otro post con toda la informacion (archivos).

Si, es muy frecuente en las
primeras alphas que Nautilus
explote en el medio del aire y
ahí automaticamente sale el
pop-up de apport preguntando
si querés reportar un bug.
Otra forma de invocarlo es
mediante el comando

```
ubuntu-bug
```

añadiendo el PID del proceso
que funciona erraticamente.

---

### Post by z37a on 2009-10-06
El Cd esta bien grabado, doy fe, de echo gracias a ese CD que grabe hace unos dias estoy usando en esta misma PC Karmic. Alt+Ctrl+F1 no va a pasar nada, pro que no inicia ni el Kernel, no aparece el usplash ni nada, muere en la imagen del bootcd al presionar enter, queda congelado ahi mismo. Con alternate no probe, por que la idea era probar como se comportaba el hard sin instalar, de hecho asi veo como funciona antes de instalar, mas tratandose de una BETA. Es un BUG para mi, un boot cd que no inicia en determiado hardware, en la laptop esta CQ50 con lectora SATA, hdd SATA y Turion64 X2 con video nVidia no inicia, y en un Athlon64 LE1620 con chiset y grafica AMD, lectora SATA y hdd SATA funciona de 10, mismo CD. Sinembargo el i586 si funciona perfecto. Para mi es algun bug con la compilacion del amd64.

---

### Post by juancarlospaco on 2009-10-07
Kernel parameters

**noapic nolapic noapm acpi=off debug**

---

### Post by z37a on 2009-10-07
> **juancarlospaco said:**
> Kernel parameters

**noapic nolapic noapm acpi=off debug**

Voy a probarlo, pero aun asi, como puede ser que con el i586 inicie sin problemas y con AMD64 no? Aparte con Jaunty funciona de 10, el problema es solo con Karmic AMD64

---

