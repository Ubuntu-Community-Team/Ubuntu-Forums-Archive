---
title: "Error VirtualBox al actualizar kernel en Ubuntu 18.04"
date: 2019-08-01
forum: Centroamerica Team
---

### Post by gamor on 2019-08-01
Hoy me ha saltado una actualización del kernel de mi Ubuntu 18.04 y una vez realizada me sale un error en Virtualbox al iniciar cualquier MV:

[I]Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/voboxdrv. Please reinstall virtualbox-dkms package and load the kernel module by executing

'modprobe vboxdrv'

as root.

where: suplibOsinit what:3
VERR_VM_DRIVER_NOT_INSTALLED (-1908) - The support driver is not installed. On Linux, open returned ENOENT.

[/I]He seguido las instrucciones de varios blogs:

[FONT=Arial]Ejecutar: sudo modprobe vboxdrv (me indica que comando desconocido)[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]- sudo apt update[/FONT]
[FONT=Arial]- sudo apt install --reinstall linux-headers-$(uname -r) virtualbox-dkms dkms (salen errores al final de la instalación)[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]He desinstalado virtualbox-dkms con los siguientes comandos:[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]- sudo apt remove virtualbox-dkms[/FONT]
[FONT=Arial]- sudo apt remove --purge virtualbox-dkms[/FONT]
[FONT=Arial] [/FONT]
[FONT=Arial]Y lo he vuelto a instalar con:[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]- sudo apt install -y virtualbox-dkms y me sale el siguiente error (salen también errores y no termina de instalarlo correctamente)

Gracias[/FONT]

---

### Post by marcoloco01 on 2020-05-16
Uff tiene mala pinta, te recomiendo que lo desinstales y lo vuelvas a instalar pero directamente desde la página oficial de virtualbox.

Llevo tiempo siguiendo la página de [https://vivaubuntu.com](https://vivaubuntu.com) que está muy bien y tienen un tutorial de como hacerlo:
[https://vivaubuntu.com/virtualbox-en-ubuntu-20-04-lts-instalar/](https://vivaubuntu.com/virtualbox-en-ubuntu-20-04-lts-instalar/)

Aquí te explican desde como desinstalarlo y como volverlo a instalar.

Espero haberte ayudado.

---

