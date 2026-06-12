---
title: "Sugerencia para el Ubuntu Brainstorm..."
date: 2009-09-23
forum: Comunidad
---

### Post by atari130xe on 2009-09-23
Gente hace rato me viene rondando la posibilidad de la creacion de paquetes .deb que se integren a una instalación recién echa y SIN conexión a internet.
Que bueno sería poder contar con paquetes .deb de programas con las dependencias "satisfechas" (en lo posible) que permitan su instalación sin necesidad de estar conectado a internet y con las dependencias resueltas partiendo de cero. Serían más "pesados" en cuanto a tamaño pero cuán beneficioso sería para las instalaciones "offline". Onda PC-BSD donde tiene ports (similares a los paquetes de Linux) donde todo viene incluido (dependencias), que opinan? :P

---

### Post by juancarlospaco on 2009-09-23
Buenisimo, ...pero hay un detalle, eso ya existe de hace rato, y se llama **APT-ZIP**

*Podriamos crearle una GUI como mucho...*
:)

---

### Post by atari130xe on 2009-09-23
> **juancarlospaco said:**
> Buenisimo, ...pero hay un detalle, eso ya existe de hace rato, y se llama **APT-ZIP**

*Podriamos crearle una GUI como mucho...*
:)

Lo desconocia totalmente! voy a buscar algo más al respecto :P

---

### Post by atari130xe on 2009-09-23
> **juancarlospaco said:**
> Buenisimo, ...pero hay un detalle, eso ya existe de hace rato, y se llama **APT-ZIP**

*Podriamos crearle una GUI como mucho...*
:)

Bueno estuve pispeando y NO es la idea, esto se trata de actualización del sistema o paqueteria, pero no de la instalación de un programa especifico. yo me refiero a eso a programas (los usuales) que YA viene empaquetados en formato .deb y que partiendo de una instalación "pelada" de Ubuntu puedan ser instalados sin necesidad de bajar dependencias si las hubiere, claro existe excepciones como programas de KDE en entorno GNOME (o viceversa) porque se necesitarian bajar las librerias de cada entorno, pero miles de programas que ya están empaquetados en formato .deb habria que re armarlos considerando las dependencias necesarias para que corra determinado programa en un Ubuntu "recien instalado", a eso me refiero. :P

apt-zip: (En Debian)
> A veces nos encontramos en la situación de tener que actualizar una maquina con una conexión a internet lenta o inexistente...
Algunas veces nos viene sugerido crear un mirror Debian, otras nos viene sugerido la descarga del primer DVD o de los primeros 2 o 3 Cd's (como sabemos en sid no existe nada de esto).
Por esto es que haremos uso de una herramienta por demás cómoda para estos casos.

---

### Post by josecuervo86 on 2009-09-23
A ver si entiendo la idea: vos propones crear un "super-paquete" que contenga tanto el programa a instalar, como las dependencias (en caso de que las tuviera, y que no vinieran por defecto en la instalación normal)? Esa parece una muy buena idea

---

### Post by pablo.s on 2009-09-23
A ver si entendí: Lo que
vos querés es que por ejemplo
venga un programa empaquetado
con sus dependencias incluidas?
Por caso de VLC en su versión Mac,
que pesa 75 MB?

EDIT: Antes andaba en sincronia
con Staar, ahora con José...

---

### Post by Hei Ku on 2009-09-23
No habia un proyecto para hacer esto? Klik o algo asi?

---

### Post by juancarlospaco on 2009-09-23
Eso es lo que hace ese programa, le pedis quiero *"programaX"*:

En la PC con Internet:
ProgramaX.deb,dependencia1.deb,dependencia2.deb,dependencia3.deb------>SuperPaqueteLoco.zip

En la PC sin Internet:
SuperPaqueteLoco.zip--->ProgramaX instalado

*...y si SuperPaqueteLoco.zip es bastante pesado.*


Klik esta abandonado y tapado por los yuyos, la ultima novedad es OpenOffice 2.0 :(
Ademas pide dependencias tambien, en la misma web dice: 
*"Ubuntu users, please first run sudo apt-get install binutils libstdc++5 rpm gnome-about"*

BTW hace mucho investigue todos esos sistemas, y el mejor es [0Install, ]("http://0install.net/goals.html")
inclusive tiene un convertidor de .deb *(deb2zero)*, es OpenSource.

:)

---

### Post by pablo.s on 2009-09-23
Si, Klik es muy parecido al
funcionamiento de las imágenes
.dmg de Mac, pero no creo que
sea lo ideal para nosotros, porque
Mac es un sistema que no es tan
modular como muchos *nixes que
en ese aspecto son más óptimos.

PD: no es crítica hacia Mac, eh!

---

