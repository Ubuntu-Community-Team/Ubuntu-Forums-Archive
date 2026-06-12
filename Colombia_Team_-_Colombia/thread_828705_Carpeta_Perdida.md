---
title: "Carpeta Perdida"
date: 2008-06-14
forum: Colombia Team - Colombia
---

### Post by kvelandia on 2008-06-14
Hola, instale Gutsy y tengo algunos problemas encontrando algunas carpetas.

Particularmente la de imagenes y la de musica, aunque falta otra de documentos.

Mis archivos y carpetas estan todos es una particion aparte a la que puedo acceder desde windows y desde UBUNTU.

Como corrijo?

---

### Post by Fhernd on 2008-06-17
Hola


Si está utilizando el escritorio GNOME, haz clic en el botón **Buscar** de la barra de herramientas estándar del navegador de archivos Nautilus, y escribe el nombre del archivo o carpeta que desea encontrar.

Otra opción, es utilizar [**Meta Tracker**]("http://www.gnome.org/projects/tracker/"). Es una herramienta que indexa los metadatos de los archivos almacenados en los soportes de almacenamiento locales.

O, **[Google Desktop]("http://http://desktop.google.com/linux/")**, para indexar y buscar.


Hasta pronto.

---

### Post by kvelandia on 2008-06-17
Gracias! La manera en la que me ayudaron a solucionarlo fue reinstalando el NTFS 3G. Tuve que reinstalarlo dos veces....pero FUNCIONO!!!

---

### Post by CdK1 on 2009-06-09
Eso es porque tus "carpetas" -aka directorio estaban en una particion NTFS, de todas maneras agrega las lineas necesarias en tu /etc/fstab para que las monte automaticamente... y otra manera de buscar cosas es el comando "find" que es bastante nice ;)

---

