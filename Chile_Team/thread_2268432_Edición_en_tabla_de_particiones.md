---
title: "Edición en tabla de particiones"
date: 2015-03-08
forum: Chile Team
---

### Post by mario-chamorro on 2015-03-08
Hola, he buscado por varias partes de la web y aún no doy la solución a este problema.

Sucede  que dentro de mi ingnorancia en el tema intenté montar una partición  "ntfs" con la aplicación DISCOS en Ubuntu 14.10, lo que no sabía es que  esta me daría sólo un montaje temporal en /mnt/"nombre de la partición".  Lo intenté dos veces con dos nombres distintos, primero (11A58.....) y  luego con el nombre de RESPALDO.  Al reiniciar las particiones no  montaban dándome un error al comenzar Ubuntu, aquí la imagen de la  primera.
[ATTACH=CONFIG]260534[/ATTACH]

Al dar la opción "S" o sea de no montar la partición y seguir con la carga de Ubuntu me carga sin problemas.
Instalé  Gparted para corregir el problema con el que pude montar  definitivamente la partición, pero al reiniciar me seguía dando el  error.

Al reingresar a Ubuntu (aquí creo que la cagué) me di  cuenta las carpetas "11A58...." y "RESPALDO" seguían en /mnt, así que  las eliminé por consola con el comando "rmdir -p" lo que pensé que  supuestamente me dejaría de dar ese error en el arranque, pero no fue  así.

Ya tengo la partición montada sin problemas, pero ese error me lo sigue dando al inicio ¿Qué debo hacer?

Saludos.

---

### Post by Patriciologico on 2015-04-27
Las agregaste en /etc/fstab ?

---

