---
title: "Actualitzacions amb USB en live"
date: 2008-03-17
forum: Catalan Team
---

### Post by Curial on 2008-03-17
Salutacions a tothom,

Tinc el portàtil funcionant amb una USB en mode live i sempre o gairebé sempre que l'actualitzo em surt un missatge E:cupsys: error en la post instal·lació.....

Haig de dir que la primera vegada vaig haver de carregar altre cop el sistema a la USB perquè va petar, al segon intent vaig provar d'anar actualitzant poc a poc en varies vegades i va anar millor.

El cas es que no se si val la pena anar actualitzant perquè cada cop que ho faig no se realment si me l'estic jugant.

Que em recomaneu companys/es?

Salut

---

### Post by menut on 2008-03-25
Prova a actualitzar evitant el paquet cupsys: sel·lecciona tots els altres.

---

### Post by Curial on 2008-03-27
Gràcies Menut, he fet com m'has dit i fa l'actualització sense problemes.
He desmarcat les quatre actualitzacions del cupsys i m'ha fet l'actualització dels 85 paquets restants perfectament.

L'únic és que no se si d'alguna manera puc fer perquè no s'intenti actualitzar el cupsys en endavant, Cada cop que intento actualitzar me'ls torna a treure.

Salut!

---

### Post by papapep on 2008-03-27
Quina versió del sysv-rc tens instal·lada?

```
sudo aptitude search sysv-rc
```

i 

```
sudo apt-cache show sysv-rc
```

---

### Post by Curial on 2008-03-27
Bona nit papapep,:mad:
:lolflag:

Aquí va el que m'ha sortit:
________________________________________________________________
ubuntu@ubuntu:~$ sudo aptitude search sysv-rc
i   sysv-rc                         - System-V-like runlevel change mechanism   
p   sysv-rc-bootsplash              - Bootsplash patches for rc files           
p   sysv-rc-conf                    - SysV init runlevel configuration tool for 
ubuntu@ubuntu:~$ sudo apt-cache show sysv-rc
Package: sysv-rc
Priority: required
Section: base
Installed-Size: 272
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian sysvinit maintainers <pkg-sysvinit-devel@lists.alioth.debian.org>
Architecture: all
Source: sysvinit
Version: 2.86.ds1-14.1ubuntu31
Replaces: file-rc, sysvinit (<< 2.85-1)
Suggests: sysv-rc-conf, bum
Conflicts: file-rc
Filename: pool/main/s/sysvinit/sysv-rc_2.86.ds1-14.1ubuntu31_all.deb
Size: 57288
MD5sum: c9d9b415341b55492e434cb6341ad08b
SHA1: b6edb9116406f2d544920fc656d2019d35264044
SHA256: 84a6a91e69fe97bf04ad3776866f78ce71f8c24acb065b680489cc1fef879e35
Description: System-V-like runlevel change mechanism
 This package provides support for the System-V like system
 for booting, shutting down and changing runlevels,
 configured through symbolic links in /etc/rc?.d/.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
_______________________________________________________________

---

### Post by Curial on 2008-03-27
> **Curial said:**
> Bona nit papapep,:mad:
:lolflag:



Aquest smilers no sé d'on han sortit.:confused:

---

### Post by papapep on 2008-03-27
I del cupsys, quina versió tens?

---

### Post by Curial on 2008-04-01
> **papapep said:**
> I del cupsys, quina versió tens?

Doncs pel que veig al synaptic: 1.3.2-1ubuntu7.3

:---)

---

