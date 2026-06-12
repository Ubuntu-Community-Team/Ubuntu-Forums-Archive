---
title: "Help! I can't open any files on hdb :(Solved)"
date: 2005-11-28
forum: Desktop Environments
---

### Post by ixus_123 on 2005-11-28
Hello.  I have just installed Breezy & most of the extra applications using Automatix (great time saver btw).

My system resides on hda & all my media lives on hdb1 - basically all my movies, pictures, mp3s.

Everyhting on this was root so I couldn't edit or delete anyhing so I typed in

sudo chmod -R 666 /media/hdb1

hoping everyone would get read/write access but now every icon I click turns into a defualt gnome icon - folders, files, the lot.

How do I save my media?

---

### Post by ixus_123 on 2005-11-28
ISO used to be a folder :(

[IMG]http://img.photobucket.com/albums/v284/ixus_123/screenshots/help.png[/IMG]

---

### Post by ixus_123 on 2005-11-28
A restart seems to have made my file readable again although root still owns everything

---

### Post by xmastree on 2005-11-28
What's your fstab entry for hdb1?

It ought to be
```
/dev/hdb1	/media/hdb1	vfat	umask=0000	0	0
```
That's assuming it's FAT32, which it will need to be if you want read/write access.

---

### Post by aysiu on 2005-11-28
Can you post the output of ```
sudo fdisk -l
```?

---

### Post by Hairy_Palms on 2005-11-28
simple way id solve this is first type in a terminal 
sudo nautilus
this launches nautlius as root then you can just make your user the owner and give everyone write access.

---

### Post by ixus_123 on 2005-11-28
[QUOTE=aysiu]Can you post the output of ```
sudo fdisk -l
```?[/QUOTE]
```
Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2590    20804143+  83  Linux
/dev/hda2            2591       19929   139275517+   5  Extended
/dev/hda5            2591       19611   136721151   83  Linux
/dev/hda6           19843       19929      698796    b  W95 FAT32
/dev/hda7           19612       19842     1855476   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14946   120053713+   b  W95 FAT32

Disk /dev/sda: 20.0 GB, 20000268288 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           5       40131    0  Empty
/dev/sda2   *           6        2431    19486845    b  W95 FAT32

```

---

### Post by ixus_123 on 2005-11-28
[QUOTE=Hairy_Palms]simple way id solve this is first type in a terminal 
sudo nautilus
this launches nautlius as root then you can just make your user the owner and give everyone write access.[/QUOTE]
Thanks :)

I tried that but it wont let me change the owner from root.  I tried checking th4e boxes below so everyone can write & it wouldn't let me do that either

---

### Post by ed_d on 2005-11-28
From Terminal, sudo chown username:username directoryname

---

### Post by aysiu on 2005-11-28
Can't you just ```
sudo umount /media/hdb1
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
``` Copy in this line:```

/dev/hdb1  /media/hdb1  vfat   umask=000   0    0
``` Save and then ```
sudo mount -a
```

?

---

### Post by ixus_123 on 2005-11-28
[QUOTE=ed_d]From Terminal, sudo chown username:username directoryname[/QUOTE]
Sorry, should one of those user names be root?

I took it to mean the following & typed:

```
stan@mitx:~$ sudo chown stan:stan -R /media/hdb1
Password:
chown: changing ownership of `/media/hdb1': Operation not permitted
chown: changing ownership of `/media/hdb1/Music': Operation not permitted

```

now terminal is reeling of the same message for every file in hdb2 (about 120gb)

---

### Post by ixus_123 on 2005-11-28
[QUOTE=aysiu]Can't you just ```
sudo umount /media/hdb1
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
``` Copy in this line:```

/dev/hdb1  /media/hdb1  vfat   umask=000   0    0
``` Save and then ```
sudo mount -a
```

?[/QUOTE]
I have no idea - this is a learnign curve for me :)

Thanks for the tip & I'll give it a try now :)

(well once F-spot finishes importing pictures)

---

### Post by ixus_123 on 2005-11-28
That worked a treat - thankyou very much :)

---

### Post by aysiu on 2005-11-28
[QUOTE=ixus_123]That worked a treat - thankyou very much :)[/QUOTE] Awesome. Just for future reference, partitions get mounted with certain permissions. Folders and files (not other partitions) can be chmoded or chowned.

---

