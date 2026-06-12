---
title: "Is it possible to name partitions in Computer?"
date: 2005-07-06
forum: Desktop Environments
---

### Post by foxy123 on 2005-07-06
I'd like to have names rather than ```
33G Hard Drive: 33G Media 
``` Is is possible to do?

---

### Post by intangible on 2005-07-06
For ext3 or ext2, **e2label /dev/partition label**

For reiserfs: **reiserfstune -l label /dev/partition**

I labeled my reiserfs partitions, makes life a lot easier.

---

### Post by foxy123 on 2005-07-06
what about FAT32?

---

### Post by intangible on 2005-07-06
FAT32: **sudo apt-get install mtools** and then **man mlabel**

---

### Post by frodon on 2005-07-07
thanks intangible, I didnt know that's possible. (... I forgot that nothing is impossible with linux !!!)

---

### Post by foxy123 on 2005-07-07
[QUOTE=intangible]FAT32: **sudo apt-get install mtools** and then **man mlabel**[/QUOTE]
man is not very helpful :( How does it actually work? I tried to get a existing label but it fails:
```
 mlabel -s d:
Drive 'D:' not supported
Cannot initialize 'D:'
mlabel: Cannot initialize drive
```

---

### Post by SNo0py on 2005-07-07
[QUOTE=foxy123]man is not very helpful :( How does it actually work? I tried to get a existing label but it fails:
```
 mlabel -s d:
Drive 'D:' not supported
Cannot initialize 'D:'
mlabel: Cannot initialize drive
```[/QUOTE]

... because there is no d: drive under Linux.... you want to read something about mounting and mount-points!

---

### Post by foxy123 on 2005-07-07
[QUOTE=SNo0py]... because there is no d: drive under Linux.... you want to read something about mounting and mount-points![/QUOTE]
well, I know that, it's just said in man mlabel:
```
Description
       The mlabel command adds a volume label to a disk. Its syntax is:
       mlabel [-vcsn] [-N serial]** [COLOR=Red]drive:[/COLOR]**[new_label]
```

---

### Post by intangible on 2005-07-07
**sudo fdisk -l**

You are looking for "Device", your "drives" are named something like **/dev/hdd1** under Ubuntu, after you get that, then do this:

**sudo mlabel -s /dev/hdd1** should show your current label for the drive
**sudo mlabel /dev/hdd1:new_label** should set a new one

I apoligize, but I don't have any fat32 partitions here to try this out on.

---

### Post by MetalMusicAddict on 2005-07-07
Thanx a bunch. I was wondering abot this. :)

---

### Post by foxy123 on 2005-07-07
[QUOTE=intangible]**sudo fdisk -l**

You are looking for "Device", your "drives" are named something like **/dev/hdd1** under Ubuntu, after you get that, then do this:

**sudo mlabel -s /dev/hdd1** should show your current label for the drive
**sudo mlabel /dev/hdd1:new_label** should set a new one

I apoligize, but I don't have any fat32 partitions here to try this out on.[/QUOTE]

I have tried it before:
```
$ sudo mlabel /dev/hda6:Music
Mtools version 3.9.9, dated 3 March 2003
$ sudo mlabel -s /dev/hda6
Mtools version 3.9.9, dated 3 March 2003
Usage: mlabel [-vscVn] [-N serial] drive:

``` 
it does not seem to work :(

---

### Post by intangible on 2005-07-07
What does **sudo mlabel /dev/hda6** do? (no options, no label) it should prompt you for a new label,

---

### Post by foxy123 on 2005-07-07
[QUOTE=intangible]What does **sudo mlabel /dev/hda6** do? (no options, no label) it should prompt you for a new label,[/QUOTE]
```
$ sudo mlabel /dev/hda6
Mtools version 3.9.9, dated 3 March 2003
Usage: mlabel [-vscVn] [-N serial] drive:
```

---

### Post by MetalMusicAddict on 2005-07-07
Aww man..."Reiserfstune is not allowed to be run on mounted filesystem." Sux. :(

My os drive is called "Filesystem". Wanted to change it.

I did a "sudo reiserfstune -l label /dev/hda2" and it told me the above.

---

### Post by intangible on 2005-07-07
Just boot from a linux cd and do so

---

