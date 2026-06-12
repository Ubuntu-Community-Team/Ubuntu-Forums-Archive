---
title: "Necessito un cop de mà (AntiVir)"
date: 2008-10-17
forum: Catalan Team
---

### Post by Satboy on 2008-10-17
Bon dia!
 Ahir vaig instal.lar l'antivirus "antivir-workstation-pers-2.1.12-19" per mitjà de la cònsola.El problema que tinc ara és que el vull desinstal·lar ja que no té interfície gràfica, i no sé com fer-ho.Em podeu donar un cop de mà?
 Al Synaptic no m'hi surt, i no hi ha cap arxiu "uninstall" a dins de la carpeta instal.lada (Fitxer d'arxius-> usr -> lib-> AntiVir)

 A10 i gràcies!!

David

---

### Post by _DarkEagle_ on 2008-10-17
Suposo que a l'hora d'instal·lar-lo vas fer un:

./configure
make
make install

Si es així .. pots provar a fer un:

make uninstall

Salut !

---

### Post by Satboy on 2008-10-17
> **_DarkEagle_ said:**
> Suposo que a l'hora d'instal·lar-lo vas fer un:

./configure
make
make install

Si es així .. pots provar a fer un:

make uninstall

Salut !

 Gràcies Àliga,
 Això ja ho he provat però no m'ha funcionat.A continunació passo les instruccions d'instal·lació a veure si algú en treu l'aigua clara:

 ==============
 Installation
==============

If you have any key files, you can put them in the same
directory as the AntiVir for UNIX install files and they
will be copied into /usr/lib/AntiVir automatically. Make
sure that the permissions of the key files are correct.

[B]Login as root, change to the directory containing the
AntiVir for UNIX install files and run the install script[/B].

**./install**

The script will do the following
- copy files to /usr/lib/AntiVir
- copy configuration files to /etc
- create links in /usr/bin and /usr/sbin (if desired)
- create links in rc.d directory (if desired)
- run a configuration script (if desired)

 A10 i gràcies de 9!

David

---

### Post by papapep on 2008-10-17
El text que has enganxat ja t'ho "canta":
> 
- copy files to /usr/lib/AntiVir

esborra el directori /usr/lib/Antivir i tot el seu contingut.

```
sudo rm -r /usr/lib/AntiVir
```

> - copy configuration files to /etc

Busca dins l'script d'instal·lació quins fitxer ha copiat a /etc i esborra'ls (de /etc, no de l'script).

> 
- create links in /usr/bin and /usr/sbin (if desired)

Elimina els enllaços creats a /usr/bin i a /usr/sbin.

- create links in rc.d directory (if desired)

mira si tens algun enllaç dins /etc/init.d que faci referència a antivir. Si en tens, atures el servei (suposant que el servei es diu "AntiVir"):

```
sudo update-rc.d AntiVir stop
```

i el deshabilites:

```
sudo update-rc.d AntiVir remove
```

- run a configuration script (if desired)

Aquí no sembla que hi hagi res a fer.

Per cert, Satboy, recorda que cal posar títols descriptius al fil.

---

