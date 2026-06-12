---
title: "Dpkg not working. No fixes on this forum could help me."
date: 2005-08-14
forum: Desktop Environments
---

### Post by Donovan on 2005-08-14
Well, I don't know how the problem started but right now i cannot install any .deb file on my machine. Using apt-get, synaptic, or dpkg directly i get this error:

```
 no se puede abrir el fichero de lista de ficheros del paquete `dpkg': Error de entrada/salida
Se encontraron errores al procesar:
 xyz.deb
Proceso detenido por haber demasiados errores.
``` 

Sometimes it also puts and the end: 
```
E: Sub-process /usr/bin/dpkg returned an error code (1)
``` 

I have tried with apt-get install -f, dpkg --configure -a, apt-get clean, autoclean, update, etc. Nothing works in any combination. Also I have tried to reinstall dpkg and dselect but i can't thanks to the error.

I used "df" and all my partitions have more than enough space, I can't find a similar situation on someone on Google or on this forum, so if anyone could give me a solution besides reinstalling Ubuntu that would be nice :P.

Thanks.

---

### Post by heimo on 2005-08-14
This can bork your package management and may not help at all. And this is what I would do:

 ```
sudo rm /var/lib/dpkg/info/xyz*
sudo apt-get --purge remove xyz
sudo apt-get install xyz
``` 

where xyz is package name from errors you get

---

### Post by Donovan on 2005-08-14
I cannot even remove programs :'(. I used your instructions with gtkpod (just to test, i dont have my iPod right now ;)) and i get the same error:

```
Donovan@PCGrande:~$ sudo apt-get --purge remove gtkpod
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
Los siguientes paquetes se ELIMINARÁN:
  gtkpod*
0 actualizados, 0 se instalarán, 1 para eliminar y 0 no actualizados.
Necesito descargar 0B de archivos.
Se liberarán 1167kB después de desempaquetar.
¿Desea continuar [S/n]? S
(Leyendo la base de datos ...
dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`gtkpod', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.
dpkg: error al procesar gtkpod (--purge):
 no se puede abrir el fichero de lista de ficheros del paquete `dpkg': Error de entrada/salida
Se encontraron errores al procesar:
 gtkpod
Proceso detenido por haber demasiados errores.
E: Sub-process /usr/bin/dpkg returned an error code (1)
``` 

I hope that the spanish verbose wont stop people to see the error :(

---

### Post by heimo on 2005-08-15
[QUOTE=Donovan]
I hope that the spanish verbose wont stop people to see the error :([/QUOTE]

Did you try all the steps? The rm-part too? Si, Spanish makes it harder to understand at least for me... :) I don't know for sure if this is same problem I've had sometimes.

---

### Post by RastaMahata on 2005-08-15
[QUOTE=heimo]Did you try all the steps? The rm-part too? Si, Spanish makes it harder to understand at least for me... :) I don't know for sure if this is same problem I've had sometimes.[/QUOTE]
 (s)he has an input/output error in dpkg.

weird though...
please type this and post the output here:```
cat /etc/apt/sources.list
```

(English speakers, please ignore the following): Reiniciaste el computador a la mala? Lo apagaste/reiniciaste mal en algun momento? Se te fue la luz o algo asi?

---

### Post by Donovan on 2005-08-15
OK the cat of my sources is:

```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main r estricted


deb http://ve.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://ve.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ve.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://ve.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multive rse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse  restricted
``` 

Exactly like the guide says.

(keep ingoring this ;)): La tuve que apagar a las malas 2 veces por el error de RenderAccel que me empezo a dar pero ya lo desactive y en el boot no me da otro error o me dice que haya problemas con el sistema de archivos.

---

