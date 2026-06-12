---
title: "Problema amb els DVD casolans"
date: 2008-11-08
forum: Catalan Team
---

### Post by carles84 on 2008-11-08
Hola, fa poc vaig instalar l'Ubuntu 8.10 (abans tenia el 8.04) i des de que ho he fet no puc fer anar els DVD grabables. Al principi no anaven cap, però he conseguit fer anar els DVDs comercials (películes, etc) però quan agafe un DVD dels que jo havia gravat anteriorment em diu que no els pot montar, o en alguns casos obri el DVD però quan vaig a reproduir-ho al VLC (o qualsevol altre) em diu que no tinc permís.

Us pose les dades que crec que necessitareu per a saber què tinc i si en cal alguna més, després la copie.

Moltes Gràcies

> 
 *-cdrom:0
       description: DVD-RAM writer
       product: DVD-RAM GSA-H58N
       vendor: HL-DT-ST
       physical id: 2
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.03
       serial: [HL-DT-STDVD-RAM GSA-H58N1.0307/12/11 7U02
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom


  *-cdrom:1
       description: CD-R/CD-RW writer
       physical id: 3
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd1
       logical name: /dev/sr1
       logical name: /media/cdrom1
       capabilities: audio cd-r cd-rw
       configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready

---

### Post by open-pitu on 2008-11-09
Bones!
Has provat de montar-ho manualment des del terminal?

[INDENT]sudo mount -t iso9660,udf /dev/scd0 /media/cdrom0 [/INDENT]
[INDENT]sudo mount -t iso9660,udf /dev/scd1 /media/cdrom1[/INDENT]

Ja diràs si t'ha funcionat.

---

### Post by carles84 on 2008-11-09
No va, em diu

> root@Carles:~# sudo mount -t iso9660,udf /dev/scd0 /media/cdrom0 
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       En alguns casos, es pot trobar informació útil a syslog,


---

### Post by slink on 2008-11-10
crec que és el mateix que em passa a mi

[http://ubuntuforums.org/showthread.php?t=867793](http://ubuntuforums.org/showthread.php?t=867793)

no atorga privilegis als dvd's, diguem-ne, casolans... :-\"

només s'obren/reprodueixen per en root :confused:

---

### Post by oriolsbd on 2008-11-10
Hola, només per comprovar que és el mateix que indica l'slink, què et diu si fas :
```
ls -l /media/cdrom
```

També adjunta el que tens al fitxer /etc/fstab.

Responent al que pregunta l'slink en el seu fil, per poder entrar dins un directori, apart de tenir permisos de lectura s'ha de tenir permisos d'execució. Si no, només podràs llistar quins fitxers hi ha dins.

Salut!

---

### Post by carles84 on 2008-11-11
> root@Carles:~# ls -l /media/cdrom
lrwxrwxrwx 1 root root 6 2008-11-08 15:51 /media/cdrom -> cdrom0
root@Carles:~# 


> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=26327a8a-d3a0-4374-bf7b-2faf8b0941a8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=922e1e82-2842-416a-b085-23c65a332af1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

a vore si serveix d'alguna cosa, xD

---

### Post by oriolsbd on 2008-11-11
Hola, el fitxer fstab el veig bé. Volia veure si tenies activat el paràmetre "exec", i veig que sí.

Quant al "ls", en comptes del que t'he comentat abans, fes:
```
cd /media/cdrom
ls -l
```

Encara que, pel que tens al fstab, suposo que els subdirectoris sí que et tindran permisos d'execució (i de lectura, clar).

---

