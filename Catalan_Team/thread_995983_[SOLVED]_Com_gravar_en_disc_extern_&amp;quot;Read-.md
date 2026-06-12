---
title: "[SOLVED] Com gravar en disc extern &amp;quot;Read-only file system&amp;quot;"
date: 2008-11-28
forum: Catalan Team
---

### Post by jinglada on 2008-11-28
Tinc un disc extern de proteccions del Mac que es va morir i ara puc recuperar les dades però no em deixa gravar-n'hi de noves.

joan@joan-laptop:/media/hfs-1$ ls -l
total 3024
-rw-r--r-- 1 99 99   13824 2008-08-17 03:16 Desktop DB
-rw-r--r-- 1 99 99   44802 2008-08-17 02:59 Desktop DF
-r-xr-xr-x 1 99 99 3032245 2006-07-06 03:23 Hard Drive Manual_multi_5 sJuly.pdf
drwxr-xr-x 1 99 99      34 2008-09-17 01:29 protec-1
joan@joan-laptop:/media/hfs-1$ sudo chown joan:joan protec-1
chown: s’està canviant el propietari de «protec-1»: **Read-only file system**
joan@joan-laptop:/media/hfs-1$ 

I aquest és el format:

joan@joan-laptop:/media/hfs-1$ sudo fdisk -l
...
Disc /dev/sdb: 250.0 GB, 250059350016 octets
255 heads, 63 sectors/track, 30401 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000
El disc /dev/sdb** no conté una taula de particions vàlida**
joan@joan-laptop:/media/hfs-1$ 

Què he de fer per poder-hi gravar?
Gràcies a la bestreta,
Joan

---

### Post by papapep on 2008-11-28
A veure com el munta..?

```
cat /etc/fstab
```

---

### Post by jinglada on 2008-11-28
> **papapep said:**
> A veure com el munta..?

```
cat /etc/fstab
```


joan@joan-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7c97fe75-576a-4e19-a86e-06f45a077fb2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=5de44525-5115-4e83-8af3-9af0102ab58b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
joan@joan-laptop:~$

No hi surt, oi? I ara mateix n'estic copiant fitxers...

---

### Post by PatrickVogeli on 2008-11-28
que sapigui, l'etc/fstab no es canvia dinamicament. Els discs durs externs i tot això es munta a traves de hal, dbus, udev o alguna historia d'aquestes, no?

---

### Post by oriolsbd on 2008-11-29
Al fitxer "fstab" se li defineix com s'ha de muntar els FileSystem, i al "mtab" hi ha la informació dels FileSystem muntats actualment. Pots enviar-nos el contingut del fitxer "mtab"?

```
cat /etc/mtab
```

Salut!

---

### Post by jinglada on 2008-11-29
> **oriolsbd said:**
> Al fitxer "fstab" se li defineix com s'ha de muntar els FileSystem, i al "mtab" hi ha la informació dels FileSystem muntats actualment. Pots enviar-nos el contingut del fitxer "mtab"?

```
cat /etc/mtab
```

Salut!

joan@joan-laptop:~$ cat /etc/mtab
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.27-9-generic/volatile tmpfs rw,mode=755 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/joan/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=joan 0 0
/dev/sda3 /media/disk ext3 rw,nosuid,nodev,uhelper=hal 0 0
/dev/sdb3 /media/hfs-1 hfsplus rw,nosuid,nodev,uhelper=hal 0 0
joan@joan-laptop:~$

Ei, aquí si que es veu!

Gràcies,
Joan

---

### Post by oriolsbd on 2008-11-29
Doncs sí que sembla que està muntat amb rw, però l'altre missatge et deia que era read-only.

En [aquest fil]("http://ubuntuforums.org/showthread.php?t=657225") s'explica exactament el mateix cas. Sembla ser que les eines d'Ubuntu per a hfs són força "sensibles". Diuen que s'hauria de muntar el disc en un MacOS, i tancar l'equip de forma correcta. Un cop fet això segurament l'Ubuntu ja te'l detectarà bé, i el podrà muntar realment amb "rw".

Llegeix el fil que t'he passat, on està molt més ben explicat. :-)

---

