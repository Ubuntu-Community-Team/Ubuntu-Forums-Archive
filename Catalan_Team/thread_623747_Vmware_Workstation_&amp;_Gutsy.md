---
title: "Vmware Workstation &amp; Gutsy"
date: 2007-11-26
forum: Catalan Team
---

### Post by farigola on 2007-11-26
He intentat instal·lar VmWare 6 Workstation al meu equip, però tinc problemes a l'hora de fer la compilació doncs l'instaLlador no sap trobar els headers

[B]Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]   [/B] 

Aquest directori no existeix i m'he vist parat. Tinc els headers instal·lats /usr/src, al fer un canvi de directori el propi instal·ador diu que no sap trobar els headers 
Total que ara per ara no tinc idea de que fer. Cert es que hi ha la tira de comentaris en vers a Gutsy i Vmware, però no aconsegueixo instal·lar el producte.

Systema Kubuntu 7.10
Vmware 6.02

---

### Post by jerec on 2007-11-26
Has de tenir instalades les linux-headers del teu kernel
El que fa la vmware es compilar diferents moduls (vmmon, vmnet, et) a partir del teu kernel.

Tambe has de tenir instalades eines de compilacio com el gcc (build-essential)

Per cert, que mes diu el vmware-config.pl?¿ 
Aixo que ens has posat es el que surt sempre a l'hora de fer la compilacio del moduls, t'esta dient que no te cap modul pre-compilat per el kernel que fas servir i que el programa t'el farà., Nomes cal apretar "enter".
Si li falta alguna cosa, has de tenir mes text amb l'error.

---

### Post by farigola on 2007-11-26
Gràcies per el teu comentari. Això es el que surt a l'hora de fer la compilació. les eines que dius estan disponibles. El headers els tinc a /usr/src i el Kernel es el 2.6.22-14-386. En teoria en aquest directori /usr/src/linux-headers-2.6.22-14

Al arribar aquest script al punt citat llavors queda enganxat i el quecal seria dir el path de l'ubicació del kernel, però no fa res.

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

---

### Post by farigola on 2007-11-26
Després d'una bona estona he vist el problema i crec que la cosa ja funciona. Bé de fet he creat ja la primera màquina virtual.
He de dir que al verificar el Kernel actual uname -r i veure els paquets instal·lats, la cosa ja estava clara doncs com deia el script el paquet concret estava per instal·lar. Ja tinc la cosa aquesta funcionant. Ara toca verificar el comportament doncs el Virtualbox ha estat una mala experiència. De ben segur amb millors coneixements el virtualbox també ha de funcionar. Sóc un aprenent de Linux.
Toca veure, tocar i provar.

---

### Post by jerec on 2007-11-26
Quant et demani la ruta de les C header files, posali:
/lib/modules/2.6.22-14-generic/build/include 
(build, normalment es un link de /usr/src/linux-headers-2.6.22-14-generic) i apunta al directori include 
o sigui apunta a : /usr/src/linux-headers-2.6.22-14-generic/include

Nota:
2.6.22-14-generic , es el kernel que faig servir jo, comprova el kernel que tens tu i si tens el directori de les headers del kernel.

---

### Post by patrickfromspain on 2007-11-26
proba posant-li /usr/src/linux-headers-2.6.22-14-generic.

salut!

---

### Post by jerec on 2007-11-26
Patricfromspain et falta /include

fixat, el vmmon:
```

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.22-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciContext.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciDatagram.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciDriver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciDs.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciGroup.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciHashtable.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciProcess.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciResource.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciSharedMem.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
The module loads perfectly in the running kernel.

```

I ara l'altre, vmblock:
```

Building the vmblock module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmblock-only'
make -C /lib/modules/2.6.22-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/block.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/control.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/dbllnklst.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/dentry.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/file.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/filesystem.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/inode.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/module.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/stubs.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/super.o
  LD [M]  /tmp/vmware-config0/vmblock-only/vmblock.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vmblock-only/vmblock.mod.o
  LD [M]  /tmp/vmware-config0/vmblock-only/vmblock.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
cp -f vmblock.ko ./../vmblock.o
make: Leaving directory `/tmp/vmware-config0/vmblock-only'
The module loads perfectly in the running kernel.

```

Aqui tens els flamants moduls de la vmware:
```

/lib/modules/2.6.22-14-generic/misc# la
total 3836
drwxr-xr-x 2 root root    4096 2007-11-26 22:00 .
drwxr-xr-x 8 root root    4096 2007-11-26 21:59 ..
lrwxrwxrwx 1 root root      45 2007-11-26 22:00 vmblock.ko -> /lib/modules/2.6.22-14-generic/misc/vmblock.o
-rw-r--r-- 1 root root  752953 2007-11-26 22:00 vmblock.o
lrwxrwxrwx 1 root root      43 2007-11-26 21:59 vmmon.ko -> /lib/modules/2.6.22-14-generic/misc/vmmon.o
-rw-r--r-- 1 root root 1789831 2007-11-26 21:59 vmmon.o
lrwxrwxrwx 1 root root      43 2007-11-10 12:25 vmnet.ko -> /lib/modules/2.6.22-14-generic/misc/vmnet.o
-rw-r--r-- 1 root root 1362719 2007-11-10 12:25 vmnet.o

```

---

### Post by farigola on 2007-11-27
Gràcies a tots per els vostres comentaris. De fet el que vaig fer, va ser informar rutes manualment doncs les carpetes del Kernel tant la de 2.6.22-14-generic com la 2.6.22-14 existien al ordinador. Això va fer que dubtes i no veia el problema. Al revisar la llista de paquets vaig veure que aquests  no estaven instal·lats. Un cop feta l'instal·lació vaig procedir un altre cop i va funcionar a la primera. Per tant Vmware 6.02 instal·lat i per cert ara per ara funciona tot, USB, CDRom. Potser tinc un desengany en poques hores, però funciona.

Repeteixo que amb la configuració actual de AMD 64 KDE, Gutsy Virtualbox va ser un problema doncs no podia obrir cap aplicació, (només  el sistema operatiu) automàticament quedava el sistema del tot parat i sense possibilitat de finalitzar tasques actives.

---

### Post by jerec on 2007-11-27
Okis, posa solucionat [SOLVED] al fil

---

### Post by AlexzAK on 2007-12-26
> **jerec said:**
> Okis, posa solucionat [SOLVED] al fil

Can you post solution in english?

---

### Post by papapep on 2007-12-26
Put the correct header library path at the wmware compile dialog prompt.

---

### Post by Tomàs M. on 2007-12-28
> **AlexzAK said:**
> Can you post solution in english?
This is a catalan forum; you can try [http://ubuntuforums.org/showthread.php?t=591732](http://ubuntuforums.org/showthread.php?t=591732)

Good luck!

---

