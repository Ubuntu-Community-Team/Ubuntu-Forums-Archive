---
title: "Problemas amb el HDD extern"
date: 2008-10-04
forum: Catalan Team
---

### Post by tanreb20 on 2008-10-04
Hokla amics!!!

Sé que s'ha publicat moltissim sobre el tema, pero l'erro que tin jo és raro d nassos!

He provat de fer tots els passos, que si al fstab, al mtab i tot.. res d res...

Si posu el HDD al mtab i al fstab em diu que no es valid xq esta duplicat o algu aixi.. Si el poso només al fstab em diu que he de ser ROOT x poder montar-lo.

i si no poso res em surt aquest error de la imate.

Tot aiXo quan el conecto.

---

### Post by CarlesOriol on 2008-10-05
Canvia el nom del disc en güindos per que no tingui caràcters com la / o \

---

### Post by jinglada on 2008-12-13
A mi em passa que tampoc em munta el HDD extern avui quan fins ara l'havia muntat just al connectar-lo a l'USB. Dóna els següents avisos:

1r avís

No es pot muntar el volum.
No es pot muntar el volum 'hfs-1'.
Detalls
mount: només l'usuari root pot muntar /dev/sdb3 a /media/hfs-1

2n avís

No s'ha pogut muntar el volum hfs-1

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by CarlesOriol on 2008-12-13
Eps Jinglada

Normalment quan es recupera un fil vell s'acaben mesclant naps i taronges.

El disc dur que dius està en format fat, ntfs, extX....???

Has provat de muntar-lo com a root?

Pots copiar el resultat de la linia de comandes ??

Si és un disc en ntfs ha comprovat que no tingui errors? I si en té i vols muntar-lo en qualsevol cas, has provat de fer-ho amb la opció -o force??

---

### Post by jinglada on 2008-12-13
> **CarlesOriol said:**
> Eps Jinglada

Normalment quan es recupera un fil vell s'acaben mesclant naps i taronges.

Obro un altre fil, doncs?

> El disc dur que dius està en format fat, ntfs, extX....???
És un hfsplus, 
joan@joan-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
...
#Entry for /dev/sdb3 :
UUID=548230C4C2550E7D	/media/hfs-1	hfsplus	defaults,nosuid,nodev,uhelper=hal	0	0

> Has provat de muntar-lo com a root?

Pots copiar el resultat de la linia de comandes ??

Si és un disc en ntfs ha comprovat que no tingui errors? I si en té i vols muntar-lo en qualsevol cas, has provat de fer-ho amb la opció -o force??

joan@joan-laptop:~$ sudo mount /dev/sdb3
mount: el punt de muntatge /media/hfs-1 no existeix
joan@joan-laptop:~$ 
------------
No fa gaire el vaig tenir muntat; i es muntava simplement al connectar-lo.

---

### Post by oriolsbd on 2008-12-13
Això em sona. El format hfsplus és el de Mac? Em sembla recordar que el Mac deixa aquest tipus "inservible" per a altres sistemes operatius si no apagues correctament el Mac amb el disc connectat (parlo de memòria). Només "inservible" fins que no es torna a aturar correctament el Mac, no per sempre. :-)

Prova d'engegar el teu Mac, connectar el disc dur, i apagar el Mac. Ara prova de connectar el disc dur de nou al Ubuntu.

Per cert, pot ser que no calgui aturar del tot el Mac. Potser simplement n'hi ha prou a desmuntar el disc de manera correcta (és a dir, no desconnectant-lo de l'USB directament). De tota manera, primer prova-ho aturant-lo del tot.

Salut!

---

### Post by jinglada on 2008-12-14
> Això em sona. El format hfsplus és el de Mac? Em sembla recordar que el Mac deixa aquest tipus "inservible" per a altres sistemes operatius si no apagues correctament el Mac amb el disc connectat (parlo de memòria). Només "inservible" fins que no es torna a aturar correctament el Mac, no per sempre.

Prova d'engegar el teu Mac, connectar el disc dur, i apagar el Mac. Ara prova de connectar el disc dur de nou al Ubuntu.

Per cert, pot ser que no calgui aturar del tot el Mac. Potser simplement n'hi ha prou a desmuntar el disc de manera correcta (és a dir, no desconnectant-lo de l'USB directament). De tota manera, primer prova-ho aturant-lo del tot.

Et sona del fil de fa dues setmanes on parlavem de 'rw'
[http://ubuntuforums.org/showthread.php?t=995983](http://ubuntuforums.org/showthread.php?t=995983), on em derivaves a un altre fil que deia que calia desactivar el 'journaling'. El mac és mort des del 4-10-2008. El disc extern el llegia tranquil·lament amb l'Ubuntu fins fa pocs dies. És ara que no el puc muntar.

En el fil que em vas derivar deia que s'havia de crear un usuari amb la mateixa identificació que tenia en el mac. Ho vaig fer i tampoc va funcionar per 'rw' però si que el llegia.

Ara m'he connectat amb aquest usuari 'igual que el del mac' i he trobat alguna cosa que potser ens pot ajudar:

joaningladaroig@joan-laptop:~$ **sudo fdisk -l**
[sudo] password for joaningladaroig: 

Disc /dev/sda: 250.0 GB, 250059350016 octets
255 heads, 63 sectors/track, 30401 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4a645369

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1   *           1        7649    61440561   83  Linux
/dev/sda2           29667       30401     5903887+   5  Estesa
/dev/sda3            7650       29666   176851552+  83  Linux
/dev/sda5           29667       30401     5903856   82  Intercanvi Linux / Solaris

Les entrades a la taula de particions no estan en l'ordre del disc

[B]Disc /dev/sdb: 250.0 GB, 250059350016 octets
255 heads, 63 sectors/track, 30401 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000[/B]

El disc /dev/sdb no conté una taula de particions vàlida
joaningladaroig@joan-laptop:~$ **cat /etc/fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sda1 :
UUID=7c97fe75-576a-4e19-a86e-06f45a077fb2	/	ext3	relatime,errors=remount-ro	0	1
#Entry for /dev/sda3 :
UUID=208e6e73-641d-43f6-af8b-4b4495f62a58	/media/disk	ext3	defaults,nosuid,nodev,uhelper=hal	0	2
[B]#Entry for /dev/sdb3 :
UUID=548230C4C2550E7D	/media/hfs-1	hfsplus	[/B]defaults,nosuid,nodev,uhelper=hal	0	0
#Entry for /dev/sda5 :
UUID=5de44525-5115-4e83-8af3-9af0102ab58b	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0


joaningladaroig@joan-laptop:~$ **cat /etc/mtab**
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
/dev/sda3 /media/disk ext3 rw,nosuid,nodev,uhelper=hal 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/joaningladaroig/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=joaningladaroig 0 0

Sembla que hi ha una contradicció entre **dev/sdb** i **dev/sdb3**, oi?

---

### Post by jinglada on 2008-12-16
Ufffff! que bé, en quitus m'ha donat la solució en el fil [http://ubuntuforums.org/showthread.php?t=997736](http://ubuntuforums.org/showthread.php?t=997736)  i finalment l'acabo de muntar i obrir amb el "disk manager". Estava molt preocupat fins i tot m'estava mentalitzant de que potser perdria gran quantitat d'informació.
Gràcies quitus!

---

