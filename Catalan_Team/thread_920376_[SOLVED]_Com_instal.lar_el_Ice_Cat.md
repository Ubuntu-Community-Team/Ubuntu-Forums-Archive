---
title: "[SOLVED] Com instal.lar el Ice Cat???"
date: 2008-09-15
forum: Catalan Team
---

### Post by kukat on 2008-09-15
Res, he provat amb el .deb  que ve amb la web però em falten llibreries, després amb el source code i tampoc...no se que fer per instal.lar-lo!!!
l'he baixat d'aci: [http://ftp.gnu.org/gnu/gnuzilla/3.0.1-g1/](http://ftp.gnu.org/gnu/gnuzilla/3.0.1-g1/)

el error: 
kukat@kukatmaulet:~$ icecat
find: /home/kukat/.gnuzilla/: No such file or directory
./icecat-bin: error while loading shared libraries: libxcb-xlib.so.0: cannot open shared object file: No such file or directory

---

### Post by papapep on 2008-09-15
Hauries de mirar si tens instal·lada la llibreria que et demana:

> ./icecat-bin: error while loading shared libraries: **libxcb-xlib**.so.0: cannot open shared object file: No such file or directory 

```
sudo aptitude search libxcb-xlib
```

Als repositoris [hi és]("http://packages.ubuntu.com/search?keywords=libxcb-xlib&searchon=names&suite=hardy&section=all").

No sé si amb això et funcionarà, però segur que és un pas endavant.

---

### Post by kukat on 2008-09-15
ups, oblidava dir-te que tinc el gutsy gibbon!
pero a la consola m'ix que ho tinc:
kukat@kukatmaulet:~$ sudo aptitude search libxcb-xlib
[sudo] password for kukat:
p   libxcb-xlib0                    - X C Binding, Xlib/XCB interface library   
p   libxcb-xlib0-dbg                - X C Binding, Xlib/XCB interface library, d
p   libxcb-xlib0-dev                - X C Binding, Xlib/XCB interface library, d

---

### Post by tanreb20 on 2008-09-15
> **kukat said:**
> 
**p **  libxcb-xlib0                    - X C Binding, Xlib/XCB interface library   
**p**   libxcb-xlib0-dbg                - X C Binding, Xlib/XCB interface library, d
**p **  libxcb-xlib0-dev                - X C Binding, Xlib/XCB interface library, d

Aqui esta el problmea! jeje es mollt senzill!

Quan fas un search i et retorna una P davant del nom del programa(o llibraria) es que esta proposat pero no instalat, si estigués instalat sortiria una **i**

```

bernat@portatil:~$ sudo aptitude search libxcb-xlib
[sudo] password for bernat: 
**i**   libxcb-xlib0                    - X C Binding, Xlib/XCB interface library   
p   libxcb-xlib0-dbg                - X C Binding, Xlib/XCB interface library, d
**i** A libxcb-xlib0-dev                - X C Binding, Xlib/XCB interface library, d
bernat@portatil:~$ 

```

Prova a fer sudo aptitude install libxcb-xlib

---

### Post by kukat on 2008-09-15
al final he posat açò:
sudo apt-get install  libxcb-xlib0 libxcb-xlib0-dbg libxcb-xlib0-dev 

ja que l'altre no l'encontrava..jejej
Però ja esà solucionat!!!!!

PD: Com es posava el de (SOLVED) ????

---

### Post by climent on 2008-09-15
a l'inici dels teus missatges hi ha un apartat que diu "thread tools". Marca'l i marca tot seguit l'opció que diu "mark this post as solved"

---

### Post by kukat on 2008-09-15
sempre em passa el mateix!jajaja
mai recorde on està! gràcies

---

### Post by SiscoGarcia on 2008-09-15
kukat, per altres vegades recorda que ho tens a l'entrada 12 del [fil d'instruccions]("http://ubuntuforums.org/showthread.php?t=599965"), aquell que tots oblidem tan sovint ;)

---

