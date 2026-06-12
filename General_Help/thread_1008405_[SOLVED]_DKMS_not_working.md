---
title: "[SOLVED] DKMS not working?"
date: 2008-12-11
forum: General Help
---

### Post by ztrange on 2008-12-11
Well, i assume I have dkms installed because when I tried sudo patitude install dkms, It said something like 0 to be downloaded, 0 to be removed, etc.

But today, when I tried to launch my vbox XP machine, i told that very known error:

The vritualbox linux kernel driver is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

/estc/init.d/vboxdrv setup

So i did that with sudo and it suceeded:

 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                          *  done.
 * Starting VirtualBox kernel module                                             *  done.


So im wondering, shouldn't it have been solved by dkms? what happened. 

I couldn't see the boot sequence dkms message nor any other messages because they have been hidden in intrepid.

---

### Post by cariboo on 2008-12-11
For more info on dkms have a look at:

```
man dkms
```

I've never seen dkms build the vbox module.

Jim

---

### Post by ztrange on 2008-12-11
Ok, I will take a look, however, I have seen it buid the vbx module, The problem is just in my new instalation. You see, I have recently formatted everything with my brand new out of date intrepid shipit cd, but before, I had intrepid that came from a hardy upgrade and in that upgrade, dkms started building vbox. Now, maybe the problem is that i got vbox after i installed dkms (in the ubuntu intrepid installation) so, maybe thats why vbox module is not detected...

Well, anyway, thankyou, I will check the man page and see if I can come up with a solution.

---

### Post by ztrange on 2008-12-11
Well, I think I got it working, however, I will not be able to be sure until another kernel level update is relased...

With the info about the configuration files of dkms from the manpages, I figured I could just reinstall dkms and it would recognice the vbox module and I think it did:

I did sudo aptitude remove dkms and sudo aptitude install dkms.

On the install output I got:

```
mario@beula:~$ sudo aptitude install dkms
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
Se instalarán los siguiente paquetes NUEVOS:
  dkms 
0 paquetes actualizados, 1 nuevos instalados, 0 para eliminar y 0 sin actualizar.
Necesito descargar 0B/55.5kB de ficheros. Después de desempaquetar se usarán 381kB.
Escribiendo información de estado extendido... Hecho
Seleccionando el paquete dkms previamente no seleccionado.
(Leyendo la base de datos ...  
137468 ficheros y directorios instalados actualmente.)
Desempaquetando dkms (de .../dkms_2.0.20.4-0ubuntu2_all.deb) ...
Procesando activadores para man-db ...
Configurando dkms (2.0.20.4-0ubuntu2) ...
 * Running DKMS auto installation service for kernel 2.6.27-9-generic            *  vboxdrv (2.0.6)...                                                   [ OK ] 

Leyendo lista de paquetes... Hecho                   
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido       
Inicializando el estado de los paquetes... Hecho
Escribiendo información de estado extendido... Hecho
```

Im sorry it is in spanish but check the part that says:

Running DKMS auto installation service for kernel 2.6.27-9-generic
vboxdrv (2.0.6)...                                                   [ OK ] 

Now, I think there may be some option to make dkms recognice the installed modules that need dkms but I could not find it.

---

