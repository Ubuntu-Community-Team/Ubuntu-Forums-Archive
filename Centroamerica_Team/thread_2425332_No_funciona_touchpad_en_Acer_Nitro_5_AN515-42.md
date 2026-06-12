---
title: "No funciona touchpad en Acer Nitro 5 AN515-42"
date: 2019-08-24
forum: Centroamerica Team
---

### Post by mantis24 on 2019-08-24
Hola,

He instalado la versión 18.04 LST de Ubuntu en mi Acer Nitro 5 AN515-42, he podido solucionar el problema de que se congelaba al bootear colocando el "noapic" en el grub. Pero lo que no he podido hacer es que me reconozca el touchpad, si funciona al conectar un mouse USB.

Al intentar simular la instalación del "xserver-xorg-input-synaptics" me aparece el siguiente error:

```
xxxyo-Nitro-AN515-42:~$ sudo apt --simulate install xserver-xorg-input-synaptics
[sudo] contraseña para xx:
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias      
Leyendo la información de estado... Hecho
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios aún no se han creado o se
han sacado de «Incoming».
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
 xserver-xorg-input-synaptics : Depende: xserver-xorg-core (>= 2:1.18.99.901)
E: No se pudieron corregir los problemas, usted ha retenido paquetes rotos.
```

Al simular la instalacion de la dependencia faltante me sale lo siguiente:

```
xx@xx-Nitro-AN515-42:~$ sudo apt --simulate install xserver-xorg-core
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Los paquetes indicados a continuación se instalaron de forma automática y ya no son necesarios.
  fonts-liberation2 fonts-opensymbol gir1.2-geocodeglib-1.0 gir1.2-gst-plugins-base-1.0 gir1.2-gstreamer-1.0 gir1.2-gudev-1.0
  gir1.2-udisks-2.0 grilo-plugins-0.3-base gstreamer1.0-gtk3 libboost-date-time1.65.1 libboost-filesystem1.65.1
  libboost-iostreams1.65.1 libboost-locale1.65.1 libcdr-0.1-1 libclucene-contribs1v5 libclucene-core1v5 libcmis-0.5-5v5
  libcolamd2 libdazzle-1.0-0 libe-book-0.1-1 libedataserverui-1.2-2 libeot0 libepubgen-0.1-1 libetonyek-0.1-1 libevent-2.1-6
  libexiv2-14 libfreerdp-client2-2 libfreerdp2-2 libgc1c2 libgee-0.8-2 libgexiv2-2 libglu1-mesa libgom-1.0-0 libgpgmepp6
  libgpod-common libgpod4 liblangtag-common liblangtag1 liblirc-client0 liblua5.3-0 libmediaart-2.0-0 libmspub-0.1-1
  libodfgen-0.1-1 libqqwing2v5 libraw16 librevenge-0.0-0 libsgutils2-2 libssh-4 libsuitesparseconfig5 libvncclient1
  libwinpr2-2 libxapian30 libxatracker2 libxmlsec1 libxmlsec1-nss libxss1 libxvmc1 lp-solve media-player-info python3-mako
  python3-markupsafe syslinux syslinux-common syslinux-legacy usb-creator-common x11-apps x11-session-utils xbitmaps xinit
  xinput
Utilice «sudo apt autoremove» para eliminarlos.
Paquetes sugeridos:
  xfonts-100dpi | xfonts-75dpi
Los siguientes paquetes se ELIMINARÁN:
  ubuntu-desktop xorg xserver-xorg-core-hwe-18.04 xserver-xorg-hwe-18.04 xserver-xorg-input-all-hwe-18.04
  xserver-xorg-input-libinput-hwe-18.04 xserver-xorg-input-wacom-hwe-18.04 xserver-xorg-video-all-hwe-18.04
  xserver-xorg-video-amdgpu-hwe-18.04 xserver-xorg-video-ati-hwe-18.04 xserver-xorg-video-fbdev-hwe-18.04
  xserver-xorg-video-intel-hwe-18.04 xserver-xorg-video-nouveau-hwe-18.04 xserver-xorg-video-qxl-hwe-18.04
  xserver-xorg-video-radeon-hwe-18.04 xserver-xorg-video-vesa-hwe-18.04 xserver-xorg-video-vmware-hwe-18.04
Se instalarán los siguientes paquetes NUEVOS:
  xserver-xorg-core
0 actualizados, 1 nuevos se instalarán, 17 para eliminar y 53 no actualizados.
Remv ubuntu-desktop [1.417.3]
Remv xorg [1:7.7+19ubuntu7.1]
Remv xserver-xorg-video-all-hwe-18.04 [1:7.7+19ubuntu8~18.04.2]
Remv xserver-xorg-video-vmware-hwe-18.04 [1:13.3.0-2build1~18.04.1]
Remv xserver-xorg-video-amdgpu-hwe-18.04 [19.0.1-1~18.04.1]
Remv xserver-xorg-hwe-18.04 [1:7.7+19ubuntu8~18.04.2]
Remv xserver-xorg-input-wacom-hwe-18.04 [1:0.36.1-0ubuntu1~18.04.1]
Remv xserver-xorg-video-vesa-hwe-18.04 [1:2.4.0-1~18.04.1]
Remv xserver-xorg-video-ati-hwe-18.04 [1:19.0.1-0ubuntu1~18.04.1]
Remv xserver-xorg-video-radeon-hwe-18.04 [1:19.0.1-0ubuntu1~18.04.1]
Remv xserver-xorg-input-all-hwe-18.04 [1:7.7+19ubuntu8~18.04.2]
Remv xserver-xorg-input-libinput-hwe-18.04 [0.28.1-1~18.04.1]
Remv xserver-xorg-core-hwe-18.04 [2:1.20.4-1ubuntu3~18.04.1] [xserver-xorg-video-intel-hwe-18.04:amd64 xserver-xorg-video-nouveau-hwe-18.04:amd64 xserver-xorg-video-qxl-hwe-18.04:amd64 xserver-xorg-video-fbdev-hwe-18.04:amd64 ]
Remv xserver-xorg-video-fbdev-hwe-18.04 [1:0.5.0-1ubuntu1~18.04.1] [xserver-xorg-video-intel-hwe-18.04:amd64 xserver-xorg-video-nouveau-hwe-18.04:amd64 xserver-xorg-video-qxl-hwe-18.04:amd64 ]
Remv xserver-xorg-video-intel-hwe-18.04 [2:2.99.917+git20171229-1ubuntu1~18.04.1] [xserver-xorg-video-nouveau-hwe-18.04:amd64 xserver-xorg-video-qxl-hwe-18.04:amd64 ]
Remv xserver-xorg-video-nouveau-hwe-18.04 [1:1.0.16-1~18.04.1] [xserver-xorg-video-qxl-hwe-18.04:amd64 ]
Remv xserver-xorg-video-qxl-hwe-18.04 [0.1.5-2build2~18.04.1]
Inst xserver-xorg-core (2:1.19.6-1ubuntu4.3 Ubuntu:18.04/bionic-updates [amd64])
Conf xserver-xorg-core (2:1.19.6-1ubuntu4.3 Ubuntu:18.04/bionic-updates [amd64])


```


He hecho una modificacion que lei que solucionaba el problema y no solo dejo de funcionar el touchpad, sino que tampoco funcionaba el mouse usb y tuve que reinstalar todo de nuevo asi que antes de instalar pregunto.


Alguien sabe como se puede solucionar el problema? 

Espero que alguien pueda ayudarme, muchas gracias!!!


Saludos.

Mantis24

---

