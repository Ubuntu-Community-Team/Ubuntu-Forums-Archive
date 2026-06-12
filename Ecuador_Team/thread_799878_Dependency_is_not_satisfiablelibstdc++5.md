---
title: "Dependency is not satisfiable:libstdc++5"
date: 2008-05-19
forum: Ecuador Team
---

### Post by daim94 on 2008-05-19
Saludos amigos

Soy neófito en linux específicamente Ubuntu hardy heron.

Tengo un problema cuando trato de instalar los W32codecs de medibuntu:
como no tengo internet en casa los baje desde un cyber luego fui y traté de instalarlos pero me sale éste mensaje: Error: Dependency is not satisfiable: libstdc++5 y no se instala. también cuando trato de modificar el escritorio con cierta configuración (pura novelería gráfica) me sale un mensaje que necesito una mejor tarjeta (tengo una Nvidia GeForce440MX) o sino que no tengo OpenGL

Sorry: más adelante enviaré las especificaciones del equipo sobre el que estoy probando Ubuntu, me gusta la idea de trabajar producción audio-visual en ambiente linux porque tradicionalmente se trabaja sobre plataforma MacOSX o tristemente en Windows.

Seguro de contar con su ayuda....espero sus comentarios y sugerencias de lo que podría ser el problema

---

### Post by jrg_dnn on 2008-05-21
umm, es mucho mas facil en el nuevo ubuntu, lo que tines que hacer, es buscar una manera de conectar to compu al internet, llevala a la casa de un amigo o alomejor al cyber, ahi trata de hacer todos los updates possibles (es bueno tener ubuntu al dia) cuando tengas tu compu conectada al internet, abre una de las files que quieras tocar, ya sea una .mp3,  .mpeg, .ogg etc, y ubuntu te indicara que codecs son los necesarios, de ahi solo dales un check e instalalos, tadas las dependencies seran automaticamente arregladas. es asi de facil!!! :)


Jorge Alvarez

---

### Post by estebandid0 on 2008-05-22
Si lo mejor sería que lo conectes al internet, tambien te sugiero que si trabajas con multimedia instales ubuntu studio que es diseñado para personas que trabajn en Multimedia

---

### Post by rlarenas on 2008-06-09
El mensaje implica que te falta algún paquete. Como la mayoría de los programas en Linux se forman con "dependencias de paquetes", requerirás bajarte todos los paquetes vinculados. Puedes saber cuales son desde el gestor de paquetes de Synaptic (le pides buscar un programa, y generas un "scrip de descarga del paquete").

Si tienes internet, la cosa es muy fácil. Las respuestas anteriores asumen que estás conectado. Pero si no lo tienes (por la razón que sea), y debes bajarte el paquete de un ciber, o conseguiste un CD que traía el paquete principal pero  no las dependencias, etc.etc., la cosa es algo más compleja.

La solución en ese caso es crear tu propio repositorio, bajarte todos los paquetes vinculados al programa que necesitas, y hacer cargar a Synaptic desde tu mismo disco duro. El proceso está muy bien explicado en la página 
[http://ar.geocities.com/novatocba/](http://ar.geocities.com/novatocba/)


Y es buena idea la de probar la distro Ubuntu Studio si la intención es trabajar en Multimedia.
Suerte
René

---

