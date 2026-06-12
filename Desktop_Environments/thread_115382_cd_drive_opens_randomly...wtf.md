---
title: "cd drive opens randomly...??wtf"
date: 2006-01-10
forum: Desktop Environments
---

### Post by linuxden on 2006-01-10
Hey,

I have the weirdest lil prob...

I have Ubuntu 5.10 on my desktop and one of my cd/dvd drives opens randomly i am not using anything and it just pops open...

Anyone heard of what this could be?? I have never seen that b4...

---

### Post by tagg3rx on 2006-01-10
It's probaly the ghost in your machine trying to get out....


wierd issue to be sure 
does it happen when a cd is in and being played?
has it happened since you installed ubuntu or did it just start?

maybe pull the plug on your cd rom and boot once shut back down plug it back in and let it be redetected.

check your /etc/fstab to see if the cd rom entry looks somehing like 
/dev/hdc   /media/cdrom0   udf,iso9660 user,noauto  0   0

if all else fails i would consder sacraficing a live chicken while chanting some voodo.  Ubuntu is from africa after all - it probaly does have some black mojo in the kernel.

---

### Post by nalmeth on 2006-01-10
haha

I'm sorry if this is bothersome to you but its pretty funny! Try to throw any CD in and mount the drive, I imagine this would stop a feable attempt by whatever demon is haunting you to open the drive.

good luck!

---

### Post by linuxden on 2006-01-11
LMAO!!! ;o)

The daemon is really getting to me but it doesnt seem to have happnd this morning...

It is a really random occurence.... so i guess its time for the chicken heads and straw dolls... lmao

OOOOboooooontoooo} Voodoo chanting....
OOOOboooooontoooo}Ditto
BOOM BOOM BOOM   } Lots of loud drums!!!! 
OOOOboooooontoooo}Ditto
OOOOboooooontoooo}Ditto

---

### Post by cutOff on 2006-01-11
Really weird.

Can you post your /etc/fstab file?

---

### Post by Thirsteh on 2006-01-11
Had that happen to me a few years back while using Redhat 9, was hilarious. Why do you want to get rid of that? It gets you chicks! ....I think.

---

### Post by linuxden on 2006-01-12
[QUOTE=cutOff]Really weird.

Can you post your /etc/fstab file?[/QUOTE]

For sure but nothing weird there...

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda2	/media/Windows	ntfs	umask=0222 0 0
/dev/hda3	/media/FAT32	vfat	umask=000 0 0

```

It sure is weird...Will look into getting girls with a randomly opening drive... ;o)

---

### Post by merkki on 2007-10-31
I have the same problem, Anyone have the solution?

---

