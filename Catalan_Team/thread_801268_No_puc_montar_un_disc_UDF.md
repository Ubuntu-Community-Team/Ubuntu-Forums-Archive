---
title: "No puc montar un disc UDF"
date: 2008-05-20
forum: Catalan Team
---

### Post by lluisalguero on 2008-05-20
He estat googlejant per si trobaba alguna cosa, i ho he trobat a aquest mateix fòrum ([http://www.uluga.ubuntuforums.org/showthread.php?t=510748](http://www.uluga.ubuntuforums.org/showthread.php?t=510748)) i no ho puc solucionar

sortida del /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=8e84d134-32f4-4ea4-ba8b-b7b3878667fc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=8208BEE408BED5FF /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=7038585538581C82 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=76969580-fc53-4ed4-90ee-7d7b63ee5f10 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   **auto**,iso9660 user,noauto,exec 0       0
```

allà on fica **auto** en negreta, és per que he entés que s'havia de provar així...

L'anglès encara que l'entenc prou bé, hi ha cops que em perdo...si algú em vol tirar un cable..

---

### Post by lluisalguero on 2008-05-20
També he provat això

```
lluis@lluis-laptop:~$ sudo mount -t udf /dev/scd0 /media/cdrom0/
mount: dispositiu de blocs /dev/scd0 està protegit contra escriptura; es muntarà en només lectura
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       En alguns casos, es pot trobar informació útil a syslog,
        proveu dmesg | tail o així

lluis@lluis-laptop:~$ 

```

---

### Post by papapep on 2008-05-20
Prova a deixar la línia així:

```
/dev/scd0  /media/cdrom0   auto user,noauto 0       0
```

reinicia l'ordinador i a veure si va.

---

### Post by lluisalguero on 2008-05-20
> **papapep said:**
> Prova a deixar la línia així:

```
/dev/scd0  /media/cdrom0   auto user,noauto 0       0
```

reinicia l'ordinador i a veure si va.


Tampoc....

---

### Post by lluisalguero on 2008-05-20
No és una cosa de vital importància, és un dvd de música en mp3 que em va gravar un amic. Amb el finestres no he tingut cap problema.

M'ha semblat llegir que l'Ubuntu no soporta el UDF 2.5 del Windows Vista..podria ser això?

---

