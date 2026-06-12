---
title: "QR GUI:Crea etiquetas QR con software libre"
date: 2010-09-17
forum: Comunidad
---

### Post by juancarlospaco on 2010-09-17
**[CENTER][SIZE="6"]QR GUI: Crea etiquetas QR con software libre[/SIZE]**

[IMG]http://img37.imageshack.us/img37/9053/qrgui.jpg[/IMG]
[/CENTER]

[LIST]
[*][**[SIZE="3"]Que es un Codigo QR???[/SIZE]**]("http://es.wikipedia.org/wiki/C%C3%B3digo_QR")
[/LIST]

[SIZE="3"]QR GUI *(beta)* [/SIZE]
Programa de Interfaz Grafica para crear Codigos QR, 
esta escrito completamente en Python y pensado para Ubuntu. 
El programa crea el icono en:
**Aplicaciones--->Accesorios--->QR GUI**

La etiqueta terminada se puede imprimir, guardar o exportar,
abre con ImageMagicks, se guarda haciendo: 
**Click derecho sobre la etiqueta--->Save...--->nombre y formato--->OK**

[LIST]
[*]Bajo licencia GPLv3
[*]Cumple estandar internacional ISO/IEC18004 
[*]El Codigo QR es codigo abierto.
[*]Tamaño del .DEB = 55Kb, Tamaño instalado = 192Kb.
[*]100% Python
[*]No instala QT/KDELibs en Gnome, no instala GTK en KDE.
[/LIST]

**[SIZE="3"]Ejemplo: [/SIZE]**

[IMG]http://file.status.net/identica/juancarlospaco-20100914T223430-bjdrz8k.jpeg[/IMG]

[SIZE="1"]Dependencias:[I] python-tk, libnotify-bin, ubuntu-standard, python-imaging, python-imaging-tk, imagemagick

Para ver el Codigo Fuente, hay 2 maneras:
En el programa, Barra de menus--->Ayuda--->Leer codigo fuente
Con el .DEB, no hacerle doble click, sino descomprimir el .deb, 
se crean una carpeta con 2 archivos comprimidos, llamados DATA y CONTROL,
descomprimir DATA, hay esta todo el codigo fuente.
[/I][/SIZE]

**[SIZE="4"]Descarga:[/SIZE]**

```
[http://tecnicoslinux.com.ar/livecd/qrgui_1.0_all.deb]("http://tecnicoslinux.com.ar/livecd/qrgui_0.1_all.deb")
```


:)

---

### Post by guillermolisi on 2010-09-17
Muy bueno Juanca !!

Gracias !

---

### Post by juancarlospaco on 2010-09-20
Gracias a ustedes, +60 visitas ninguna queja  ;P

Me parece que anda bien, lo he probado con Android y con Symbian y los lee perfecto.

Como no sabia que poner de icono puse el icono de la pagina de Ubuntu-AR :)
*(todo sea por difundir)*

---

### Post by juancarlospaco on 2010-10-02
**Nueva Version:**

[CENTER][IMG]http://img268.imageshack.us/img268/9053/qrgui.jpg[/IMG][/CENTER]

[LIST]
[*]Soporte para Maverick Meerkat.
[*]Aceleracion opcional via Psyco.
[*]Soporte para hacer etiquetas con Ñ y áçé&#324;tó&#347;.
[*]Soporte directo para la nueva ubuntu font por defecto.
[*]Agrega opcion de establecer fuente personalizada a la gui.
[*]Correciones en la opcion english gui.
[*]Agregado de opcion de establecer el tamaño del qr code via Slider.
[*]Opcion de ocultar el Slider.
[*]Soporte para mouse wheel.
[*]Agrega opciones  extra al menu Ayuda.
[/LIST]


```
[http://tecnicoslinux.com.ar/livecd/qrgui_1.0_all.deb]("http://tecnicoslinux.com.ar/livecd/qrgui_1.0_all.deb")
```

*[SIZE="1"]Gracias a los Tester, gracias a Marco.[/SIZE]*

:P

---

### Post by atari130xe on 2010-10-02
Felicitaciones Juan carlos!!! :P

---

### Post by juancarlospaco on 2010-10-10
**Nueva Version:**

[IMG]http://img87.imageshack.us/img87/1228/gtkontk.jpg[/IMG]

*Ahora QRGUI averigua que tema de escritorio estas usando y usa los mismos colores aprox.*

[LIST]
[*]Soporte para Temas GTK, sin necesitar GTK instalado *[SIZE="1"](Hack)[/SIZE]*.
[*]Control de instancias, solo permite 1 instancia del programa.
[*]Control de permisos, no permite ejecutarlo como root, por seguridad.
[*]Chequea Version de Python en el arranque.
[*]Chequea Version de TK en el arranque.
[*]Paquete .DEB Lintian clean.
[/LIST]

```

[http://tecnicoslinux.com.ar/livecd/qrgui_1.4_all.deb]("http://tecnicoslinux.com.ar/livecd/qrgui_1.4_all.deb")

```

:P

---

### Post by alfplayer on 2010-10-10
> **juancarlospaco said:**
> Control de permisos, no permite ejecutarlo como root, por seguridad.

Pero si no se conecta por red, cómo es peligroso? O se conecta?

---

### Post by juancarlospaco on 2010-10-10
No usa la red, yo no dije que sea peligroso, no se conecta con nada,
pero es por otros motivos de seguridad local, es un *"Best Practice"*,
ademas no necesita privilegios elevados para funcionar.

:)

---

### Post by alfplayer on 2010-10-10
> **juancarlospaco said:**
> No usa la red, yo no dije que sea peligroso, no se conecta con nada,
pero es por otros motivos de seguridad local, es un *"Best Practice"*,
ademas no necesita privilegios elevados para funcionar.

:)

OK. En el futuro se podría quitar si después no hay más riesgo "local" en el código. Es útil usar el sistema y las aplicaciones como root en algunos casos.

---

### Post by picaeta on 2011-01-03
hola he descargado el programa 1.4.deb y la 1.0.deb y he probado con varios lectores pero ninguno reconoce la Ñ y áçé&#324;tó&#347; hay alguna solución

---

### Post by juancarlospaco on 2011-01-03
Intencionalmente jamas uso acentos, pero la Ñ jamas me trajo un problema...
 meh, esta pensado para poner URLs, las url no tienen acentos ni Ñ...

---

