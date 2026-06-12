---
title: "Full permissions on FAT partition"
date: 2005-12-17
forum: General Help
---

### Post by filipenetto on 2005-12-17
Hi people ...

Somebody know how I mount a FAT partition with wirte privileges ?

Tks !

---

### Post by aysiu on 2005-12-17
See the fourth link in my sig.

---

### Post by filipenetto on 2005-12-17
Ok, 

I follow the steps, but it continues with ready only permissions. Do you know why ?

Tks !

---

### Post by aysiu on 2005-12-17
[QUOTE=filipenetto]Ok, 

I follow the steps, but it continues with ready only permissions. Do you know why ?

Tks ![/QUOTE] Did you reboot?

---

### Post by filipenetto on 2005-12-17
Yes, 

I reboot, and it mount the partition, but with ready only permission.

---

### Post by aysiu on 2005-12-17
Okay. Post the output of these three commands. Let's take a look at what's going on: ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by rafa.drums on 2005-12-18
I have this problem too, only root white in fat partition...

rafa@rafa:~$ sudo fdisk -l
Password:

Disk /dev/hda: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cilindros of 16065 * 512 = 8225280 bytes

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2167    17406396    7  HPFS ou NTFS
/dev/hda2            2168        3442    10241437+  83  Linux
/dev/hda3            3443       14596    89594505    f  W95 Ext'd (LBA)
/dev/hda5            3443        9179    46082421    b  W95 FAT32
/dev/hda6            9180       13641    35840983+   b  W95 FAT32
/dev/hda7           13642       13704      506016   82  Linux swap / Solaris
/dev/hda8           13705       14596     7164958+  83  Linux
rafa@rafa:~$ df -h
Sist. Arq.            Tam   Usad Disp  Uso% Montado em
/dev/hda2             9,8G  2,7G  7,2G  28% /
tmpfs                 253M     0  253M   0% /dev/shm
tmpfs                 253M   13M  240M   5% /lib/modules/2.6.12-10-386/volatile
/dev/hda8             6,7G  1,2G  5,2G  19% /home
/dev/hda1              17G  8,5G  8,2G  52% /media/hda1
/dev/hda5              44G   38G  6,2G  87% /media/hda5
/dev/hda6              35G   24G   11G  68% /media/hda6
/dev/hda5              44G   38G  6,2G  87% /mnt/musicas
rafa@rafa:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               reiserfs notail          0       1
/dev/hda8       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda5       /media/hda5     vfat    defaults        0       0
/dev/hda6       /media/hda6     vfat    defaults        0       0
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
#/dev/hda5       /mnt/musicas   vfat umask=000 0 0
/dev/hda5        /mnt/musicas   vfat iocharset=utf8,umask=000 0 0
rafa@rafa:~$

---

### Post by filipenetto on 2005-12-18
Here.

$ sudo fdisk -l:

[COLOR="DimGray"]Disk /dev/hda: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cilindros of 16065 * 512 = 8225280 bytes

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         981     7879851   83  Linux
/dev/hda2             982        1027      369495    5  Estendida
/dev/hda5             982        1027      369463+  82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cilindros of 16065 * 512 = 8225280 bytes

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1530    12289693+   7  HPFS ou NTFS
/dev/hdb2            1531        4869    26820517+   f  W95 Ext'd (LBA)
/dev/hdb5            1531        4869    26820486    b  W95 FAT32[/COLOR]


$ df -h

[COLOR="DimGray"]Sist. Arq.            Tam   Usad Disp  Uso% Montado em
/dev/hda1             7,4G  4,7G  2,4G  66% /
tmpfs                 253M     0  253M   0% /dev/shm
tmpfs                 253M   13M  240M   5% /lib/modules/2.6.12-10-386/volatile
/dev/hdb5              26G   24G  1,9G  93% /mnt/documentos
/dev/hdb1              12G   11G  1,7G  86% /mnt/ntfs
/dev/hdc              619M  619M     0 100% /media/cdrom0[/COLOR]


$ cat /etc/fstab

[COLOR="DimGray"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
#/dev/hdb5       /mnt/documentos        vfat    iocharset=utf8,umask=000       0       0
/dev/hdb5       /mnt/documentos vfat    iocharset=utf8,umask=000        0 0
/dev/hdb1       /mnt/ntfs       ntfs    nls=utf8,umask=0222     0       0[/COLOR]

Tks ! :)

---

### Post by aysiu on 2005-12-18
[QUOTE=rafa.drums]
/dev/hda5       /media/hda5     vfat    defaults        0       0
/dev/hda5        /mnt/musicas   vfat iocharset=utf8,umask=000 0 0[/QUOTE] You have /dev/hda5 mounted twice--one with defaults. Get rid of the defaults line and reboot your computer.

---

### Post by aysiu on 2005-12-18
[QUOTE=filipenetto]
/dev/hdb5       /mnt/documentos vfat    iocharset=utf8,umask=000        0 0[/QUOTE] These mount options look good. The only thing that might be worth a try is mounting it somewhere other than the /mnt folder? Try ```
sudo umount /mnt/documentos
sudo mkdir /documentos
sudo nano /etc/fstab
``` changing the line to ```
/dev/hdb5       /documentos vfat    iocharset=utf8,umask=000        0 0
``` Saving (control-x), confirming (y), exiting (Enter), then ```
sudo mount -a
```

---

### Post by filipenetto on 2005-12-18
Okay, 

Doesn't work ... :( 

It continues without write permissions. Any other sugestions ?

---

### Post by aysiu on 2005-12-18
[QUOTE=filipenetto]
It continues without write permissions. Any other sugestions ?[/QUOTE] None.

---

### Post by filipenetto on 2005-12-18
Owww my god ... 

So, anybody can help me ?

---

### Post by aysiu on 2005-12-18
[QUOTE=filipenetto]Owww my god ... 

So, anybody can help me ?[/QUOTE] The only workaround I can think of is creating a launcher on the panel with the command ```
gksudo nautilus
``` and then going to /mnt/documentos.

---

### Post by rafa.drums on 2005-12-18
[QUOTE=filipenetto]Owww my god ... 

So, anybody can help me ?[/QUOTE]


Brother, estou com o mesmo problema!!!

Se tiver sugestão, escreva!!!

---

### Post by filipenetto on 2005-12-18
E ai cara, eh brazuca tambem ? Adicionar o MSN ai no seu perfil pra gente trocar ideia.

Ateh mais !


Translating:

"Hi man, are you brazillian too ? Adds the MSN in your profile to we talk.
See you!"

---

### Post by rafa.drums on 2005-12-20
Tá na mão!

---

### Post by filipenetto on 2005-12-21
People, 

I don't know how, but the write permissions was implemented ! 

Some day, I try do move the files, and I got it !

So, the line of the partition is this:

```
/dev/hdb5      	/documentos	vfat	iocharset=utf8,umask=000	0       0
```

Thank you for everybody !

---

