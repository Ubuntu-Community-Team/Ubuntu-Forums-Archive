---
title: "Mounting NTFS partitions."
date: 2006-06-19
forum: Desktop Environments
---

### Post by muxecoid on 2006-06-19
When I boot from LiveDVD I see NTFS partitions in nautilus drivelist, but double click causes
```

Unable to mount the selected volume.

error: device /dev/hdd1 is not removable

error: could not execute pmount

```
What needs to be done?

---

### Post by aysiu on 2006-06-20
```
sudo mkdir /windows
sudo mount -t ntfs /dev/hdd1 /windows -o nls=utf8,umask=0222
``` Then go to the /windows directory in Nautilus.

---

### Post by Kouya on 2006-06-20
Hi Ubuntu newbie here. Just installed it last night. I tried the above and when i clicked on the drive no error appears but it will not open and it reads it as 0 bytes??

---

### Post by ayoli on 2006-06-20
did you try to type aysiu's command in a term ?
something else, i think with ubuntu default kernel config you 'll not be able to write ntfs partition (read only)

---

### Post by Kouya on 2006-06-20
[QUOTE=ayoli]did you try to type aysiu's command in a term ?
something else, i think with ubuntu default kernel config you 'll not be able to write ntfs partition (read only)[/QUOTE]

In a term? sorry but what does that mean? 

Yup i know it's read only but now after mounting I can't even go in to see what files there are inside. Is there anyway to be able to read and write nfts partitions in ubuntu, like make some modifications??

oh I am not running from LiveCD..I installed it to another harddrive, a slave one.

---

### Post by maskd on 2006-06-20
[QUOTE=Kouya]In a term? sorry but what does that mean? 

Yup i know it's read only but now after mounting I can't even go in to see what files there are inside. Is there anyway to be able to read and write nfts partitions in ubuntu, like make some modifications??

oh I am not running from LiveCD..I installed it to another harddrive, a slave one.[/QUOTE]

term = Terminal

I get the same problem actually, just type in what aysiu said and it should all be well

---

### Post by Kouya on 2006-06-20
[QUOTE=aysiu]```
sudo mkdir /windows
sudo mount -t ntfs /dev/hdd1 /windows -o nls=utf8,umask=0222
``` Then go to the /windows directory in Nautilus.[/QUOTE]

sorry for a silly question but how do i "go to the /windows directory in Nautilus?"

---

### Post by ayoli on 2006-06-20
in nautilus, type CTRL L opens location bar where you type in /windows.

---

### Post by Kouya on 2006-06-20
bea@ubuntu:~$ sudo mount -t ntfs /dev/hda1 /windows -o nls=utf8,umask=0222aaa
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

i get the above error when i type in aysiu's code...eh...wat did i do wrong?

ps. how do i get that code box out like wat aysiu did?

---

### Post by Kouya on 2006-06-20
[http://wiki.linux-ntfs.org/doku.php?id=ntfsmount](http://wiki.linux-ntfs.org/doku.php?id=ntfsmount)

it says here nfts can be read and write... Does this really work? anyone tried this?

---

### Post by ayoli on 2006-06-20
the code box: when you type you msg, select the text you want and hit the format button with a #

ntfs: default ubuntu kernel is configured/compiled without ntfs write support
but ntfs partitions are readable.

about your error, are you sure your win partition is ntfs, not fat32 ?

---

### Post by Kouya on 2006-06-20
thanks for all the help ayoli...

it's definitely ntfs..not fat32. This is driving me nuts. Think I'll go sleep and try it out again tml.

---

### Post by unf on 2006-06-20
bea@ubuntu:~$ sudo mount -t ntfs /dev/hda1 /windows -o nls=utf8,umask=0222>>>>>>>>>>>>>>**aaa**<<<<<<<<<<<<<<<<< 

WHAT IS THAT???? 

sudo mkdir /windows
sudo mount -t ntfs /dev/hda1 /windows -o nls=utf8,umask=0222

Not 0222aaa

If you still have problem with mountin ntfs 

fdisk -l /dev/hda 

copy the output here.

---

### Post by Kouya on 2006-06-20
#-o whoops...unf you were right...*redfaced*

now i can access my ntfs drives already!!

=D> now to get it to be read-&-write!! thanks for the help unf and ayoli!!

---

### Post by ayoli on 2006-06-20
lol, i didn't see the 'aaa' last time :p, i guess i need to have a rest

---

### Post by muxecoid on 2006-06-21
Do you think, that NTFS writing driver is reliable?

---

### Post by aysiu on 2006-06-21
[QUOTE=muxecoid]Do you think, that NTFS writing driver is reliable?[/QUOTE]
No.

---

