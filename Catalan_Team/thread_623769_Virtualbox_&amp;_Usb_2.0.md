---
title: "Virtualbox &amp; Usb 2.0"
date: 2007-11-26
forum: Catalan Team
---

### Post by farigola on 2007-11-26
Durant el cap de setmana he tingut una lluita sense treva amb virtualbox i Gutsy (KDE).

Al instal·lar virtualbox el suport USB no surt disponible. Vaig fer la baixada de la versió gutsy non free i seguidament la seva instal·lació. Vaig instal·lar windows sense cap problema, però el sistema no podia detectar USB 

Vaig fer les meves revisions de fòrums i altres i vaig trobar que Gutsy no activa USB automàticament  i cal editar :mountdevsubfs.sh

sudo gedit /etc/init.d/mountdevsubfs.sh

Cal treure el comentari ‘# a línies

#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb

Per deixar-ho com segueix

mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

Llavors editar

sudo gedit /etc/udev/rules.d/40-permissions.rules

fer una cerca per la línia 

SUBSYSTEM=="usb_device", MODE="0664"

i fer el canvi corresponent

SUBSYSTEM=="usb_device", MODE="0666"

Bé això he de dir que funciona però ara cada cop que vaig per obrir una aplicació des de la maquina virtual el sistema queda totalment penjat, tant la màquina virtual com el propi sistema.

---

### Post by orestesmas on 2007-11-28
Hola farigola,

Em sembla que el problema és que VirtualBox utilitza la informació de /proc/usb per accedir als ports USB del host, però ara a la gutsy el /proc l'han desactivat perquè la informació sobre els USB ja està també al direcotri /sys.

Si es vol que funcionin els usb s'ha de seguir accedint als USB via el /proc. Per fer-ho n'hi ha prou en fer el que tu dius, però és més simple recuperar el /proc/bus/usb afegint la següent línia al /etc/fstab:

none            /proc/bus/usb           usbfs    defaults        0       0

O bé fer-ho a mà cada vegada amb:

sudo mount -t usbfs none /proc/bus/usb

Et voilà!

---

