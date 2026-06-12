---
title: "upgrade kdelibs-data problem"
date: 2005-04-26
forum: Desktop Environments
---

### Post by quique on 2005-04-26
When I try to update this package, i find this problem:

root@enrique:/home/quique # apt-get dist-upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
Calculando la actualización... Listo
Los siguientes paquetes se han retenido:
  libxvidcore4 mplayer-386
Se actualizarán los siguientes paquetes:
  kdelibs-data
1 actualizados, 0 se instalarán, 0 para eliminar y 2 no actualizados.
8 no instalados del todo o eliminados.
Se necesita descargar 0B/8013kB de archivos.
Se utilizarán 0B de espacio de disco adicional después de desempaquetar.
¿Desea continuar [S/n]?

Preconfiguring packages ...
(Leyendo la base de datos ...
87049 ficheros y directorios instalados actualmente.)
Preparando para reemplazar kdelibs-data 4:3.4.0-0ubuntu3 (usando .../kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb) ...
Desempaquetando el reemplazo de kdelibs-data ...
dpkg: error al procesar /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb (--unpack):
 intentando sobreescribir `/usr/share/icons/default.kde', que está también en el paquete knetworkconf
Se encontraron errores al procesar:
 /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

After that problem, the menu in KDE was missing, only desktop icon is present in panel. 

I must return to gnome, is kubuntu ready for daily use or not?

Thanks.

---

### Post by howhard1309 on 2005-04-26
Hi all,

just wanted to say that I have experienced this same bug also.

As well experiencing the above poster's problems, the error message I repeatedly get when attempting to use the update manager is:

E: /var/cache/apt/archives/kdelibs-data_4-0x1.6c7820000005ap-1363.4.0-0ubuntu3.1_all.deb:  
trying to overwrite `/usr/share/icons/default.kde', which is also in package knetworkconf

I tried apt-get remove knetworkconf, but that requires removing kubuntu-desktop as well.

Any ideas, anyone? :roll:

---

### Post by elpamperolo on 2005-04-26
read older threads

---

### Post by srss on 2005-04-26
I had the same BUG in here. Well... as an advice, do not try to uninstall this package, otherwise it will mess with your KDE... My panel icons were gone.
I used this as an excuse and reinstalled Kubuntu. But this is not at all a good thig todo.
I´m also waiting for an solution.

Elpamperolo, could you please give us the link? Thanks in advance.

---

### Post by author.psi on 2005-04-26
I have the Probem too. I want to say thanks for the link, but my english is a bit horobil (see my posts  :???:) It is diffeculd for me to find the posts here.

---

### Post by ceti on 2005-04-26
[QUOTE=author.psi]I have the Probem too. I want to say thanks for the link, but my english is a bit horobil (see my posts :???:) It is diffeculd for me to find the posts here.[/QUOTE]
 
 
Follow this one:
 
[http://www.ubuntuforums.org/showthread.php?t=28678]("http://www.ubuntuforums.org/showthread.php?t=28678")
 
ceti

---

### Post by author.psi on 2005-04-26
Thanks allot!

For German KDE Users:
[This link will help you](http://www.marcel.gamika.de/kubuntufriends/html/modules/wiwimod/index.php?page=KdelibsProblembeimUpdate&back=FehlerbehebungundBekannteFehler)

---

