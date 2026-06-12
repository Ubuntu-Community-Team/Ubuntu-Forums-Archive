---
title: "[SOLVED] Kubuntu KDE 4.1 no munta els CD"
date: 2008-10-23
forum: Catalan Team
---

### Post by Josep Maria on 2008-10-23
Hola a tots:
No voldria abusar del fòrum. Darrerament ja he escrit dos cops.
Però tinc un problema "tonto" que no se com resoldre.
Vaig instal.lar l'escriptori Kubuntu KDE 4.1. No està tan afinat com el Gnome, peta algun cop, però va bastant bé.
Per exemple l'Amarok es carrega molt més ràpid i el Konkeror va com una seda.
Però em trobo que no em munta els CD, i no veig la manera de trobar-los enlloc.
Sabeu com puc arreglar-ho?
Gràcies

---

### Post by LitusMayol on 2008-10-23
Uuuuh...Tu no saps que és abusar del fòrum! eheh Posa el meu nickname al cercador i et riuràs una estoneta! ;)



Prova d'escriure al terminal:
```
mount
``` 
i enganxa la sortida a veure que et diu.

---

### Post by indiosincracia on 2008-10-23
hardy no munta la grabadora DVD usb automaticament,
jo tinc kde 3.5.10 i es una grabadora benq DVD externa, no se si parlem del mateix?

he instal·lat "usbmount" "pmount", el "hal" ja hi era.

indiosincracia@tontet:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c8db72d0-9792-4c76-b753-587bbbaa9061 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=7549ffef-5014-42ab-be80-a2ee73e32819 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

udf,iso9660 - es per montar CD/DVD, pero no se pas com fer-ho
Merci de dreta a esquerra.

---

### Post by Josep Maria on 2008-10-23
Hola Litus idiosincracia i demes.
El que em surt es aixo

josepmaria@josepmaria-desktop:~$ mount
/dev/sda7 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-21-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
josepmaria@josepmaria-desktop:~$

---

### Post by orestesmas on 2008-10-23
No sé exactament què vols dir amb això de que "no els munta"... Vols dir que no ho fa automàticament o que dóna un error?

El procés hauria de ser el següent:

1) Poses un CD al lector, i esperes una estona
2) Apareix un missatge al "Notificador de dispositiu nou" indicant que s'ha inserit un CD
3) Cliques damunt el nom del CD i aquest s'obre amb el Dolphin, mostrant el seu contingut.

El procés no és automàtic. Cal que tu li diguis que el munti. Això és diferent al KDE 3, però ara per ara no trobo on es pot canviar en el KDE 4. Potser no es pot, i és quelcom que encara han d'implementar.

Cal tenir una mica de paciència amb el KDE 4 perquè és molt nou, incorpora un munt de noves característiques, i la seva depuració portarà cert temps encara.

---

### Post by Josep Maria on 2008-10-24
Bon dia Orestes:
És justament això, que el CD no apareix al notificador de "dispositius connectats recentment".
En canvi m'apareixen bé els disc durs USB o el pendrive.
Deu haver-hi alguna cosa que no trobo.

---

### Post by CarlesOriol on 2008-10-25
enganxa'ns el resultat de:

sudo cat /etc/fstab

---

### Post by Josep Maria on 2008-10-25
Hola Carles Oriol.
Em dona el següent:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=e27eec60-2a99-4a75-b4c6-11edef80bb46 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=a9fa55bc-b585-4eab-b746-514c6f7a412f none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by CarlesOriol on 2008-10-25
Mira si dona cap error fent el muntatge a ma:

mkdir cd
sudo mount /dev/scd0 cd

(o scd1 ja que diu que en tens 2)

---

### Post by Josep Maria on 2008-10-25
Sí, ara si que ho munta.
Gracies Carles.

---

