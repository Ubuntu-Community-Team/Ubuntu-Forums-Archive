---
title: "problema con apt-get update"
date: 2023-03-16
forum: Centroamerica Team
---

### Post by antonio715 on 2023-03-16
Buenos días,

hace ya unos años que tengo el siguiente problema al actualizar (apt-get update y upgrade):

Leyendo lista de paquetes... Hecho
W: chmod 0700 of directory /var/lib/apt/lists/partial failed - SetupAPTPartialDirectory (1: Operación no permitida)
E: No se pudo abrir el fichero de bloqueo «/var/lib/apt/lists/lock» - open (13: Permiso denegado)
E: No se pudo bloquear el directorio /var/lib/apt/lists/
W: Se produjo un problema al desligar el fichero /var/cache/apt/pkgcache.bin - RemoveCaches (13: Permiso denegado)
W: Se produjo un problema al desligar el fichero /var/cache/apt/srcpkgcache.bin - RemoveCaches (13: Permiso denegado)

cuando lo intento haciendo previamente "sudo su" obtengo:

W: El repositorio «[http://ppa.launchpad.net/cartes/drawing/ubuntu](http://ppa.launchpad.net/cartes/drawing/ubuntu) xenial Release» no tiene un fichero de Publicación.
N: Los datos de un repositorio como este no se pueden autenticar y por tanto su uso es potencialmente peligroso.
N: Vea la página de manual apt-secure(8) para los detalles sobre la creación de repositorios y la configuración de usuarios.
E:  Fallo al obtener  [http://ppa.launchpad.net/cartes/drawing/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/cartes/drawing/ubuntu/dists/xenial/main/binary-amd64/Packages)   404  Not Found [IP: XXX.XXX.XXX.XX XX]
E: No se han podido descargar algunos archivos de índice, se han omitido, o se han utilizado unos antiguos en su lugar.

entiendo que hay algún paquete que está impidiendo que pueda actualizar
Tampoco puedo actualizar a una nueva versión de ubuntu porque siempre me sale este error, actualmente no puedo instalar ningún programa (desde hace unos años)
he intentado las opciones que me dan en este blog: 
[https://rhoconlinux.wordpress.com/2014/05/23/rapidito-como-solucionar-e-no-se-pudo-abrir-el-fichero-de-bloqueo-varlibdpkglock-open-13-permiso-denegado/](https://rhoconlinux.wordpress.com/2014/05/23/rapidito-como-solucionar-e-no-se-pudo-abrir-el-fichero-de-bloqueo-varlibdpkglock-open-13-permiso-denegado/)
pero nada funcionó

alguien tiene idea de qué puedo hacer?

Gracias anticipadas.

---

### Post by naufrsb on 2023-03-16
El error esta definitivamente ligado a problemas de permisos en los directorios de apt-get. Esto es lo que impide que se actualice y se instale software.
Intente lo siguient: 

[LIST=1]
[*]Siempre escriba "sudo" antes de los comandos que esté ejecutando.
[*]Cambie los permisos de los directorios /var/lib/apt/lists y /var/cache/apt para que el usuario actual tenga acceso de escritura. Puede hacer esto con el siguiente comando: sudo chmod -R u+w /var/lib/apt/lists /var/cache/apt
[*]Ejecute el comando "apt-get clean" para eliminar los archivos de índice de paquetes descargados anteriormente.
[*]Actualice la lista de paquetes con el comando "apt-get update" y luego intente actualizar e instalar paquetes con el comando "apt-get upgrade".
[/LIST]
Espero que le haya ayudado!

---

### Post by antonio715 on 2023-03-16
después de "sudo apt-get update" obtengo (solo pego el final):

W: El repositorio «[http://ppa.launchpad.net/cartes/drawing/ubuntu](http://ppa.launchpad.net/cartes/drawing/ubuntu) xenial Release» no tiene un fichero de Publicación.
N: Los datos de un repositorio como este no se pueden autenticar y por tanto su uso es potencialmente peligroso.
N: Vea la página de manual apt-secure(8) para los detalles sobre la creación de repositorios y la configuración de usuarios.
E: Fallo al obtener [http://ppa.launchpad.net/cartes/drawing/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/cartes/drawing/ubuntu/dists/xenial/main/binary-amd64/Packages)  404  Not Found [IP: XXX.XXX.XXX.XX XX]
E: No se han podido descargar algunos archivos de índice, se han omitido, o se han utilizado unos antiguos en su lugar.

también intenté el "sudo apt-get upgrade" pero me da el error que me da siempre (pego después de decirle Sí):

Des:1 [https://repo.skype.com/deb](https://repo.skype.com/deb) stable/main amd64 skypeforlinux amd64 8.95.0.408 [126 MB]
Descargados 126 MB en 8s (15,1 MB/s)                                           
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Leyendo la base de datos ... 329070 ficheros o directorios instalados actualmente.)
Preparando para desempaquetar .../skypeforlinux_8.95.0.408_amd64.deb ...
Desempaquetando skypeforlinux (8.95.0.408) sobre (8.94.0.428) ...
Procesando disparadores para desktop-file-utils (0.22-1ubuntu5.2) ...
Procesando disparadores para bamfdaemon (0.5.3~bzr0+16.04.20180209-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Procesando disparadores para gnome-menus (3.13.3-6ubuntu3.1) ...
Procesando disparadores para mime-support (3.59ubuntu1) ...
Procesando disparadores para hicolor-icon-theme (0.15-0ubuntu1.1) ...
Configurando opera-stable (82.0.4227.43) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error al procesar el paquete opera-stable (--configure):
 el subproceso instalado el script post-installation devolvió el código de salida de error 1
Configurando ubuntu-advantage-tools (27.13.6~16.04.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error al procesar el paquete ubuntu-advantage-tools (--configure):
 el subproceso instalado el script post-installation devolvió el código de salida de error 1
Configurando motion (3.2.12+git20140228-8build1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error al procesar el paquete motion (--configure):
 el subproceso instalado el script post-installation devolvió el código de salida de error 1
Configurando skypeforlinux (8.95.0.408) ...
Se encontraron errores al procesar:
 opera-stable
 ubuntu-advantage-tools
 motion
E: Sub-process /usr/bin/dpkg returned an error code (1)

alguna otra idea? Gracias

---

