---
title: "2 Hdd's and Ubuntu?"
date: 2006-01-02
forum: General Help
---

### Post by s_spiff on 2006-01-02
I have two hdd's , one a 80 GB , on which I installed unbuntu [ it didn't have any partitions ] and the other a 120 GB on which I hav my data, windows etc. I have the 120 as master and 80 as slave, though in the bio's, modded the boot device to hhd1 [ 80 ] so that Linux is loaded. Now In linux, I cannot find the 120 gb folders. Can someone tell me as to where I can find my files and etc. of the 120 gb?

---

### Post by installer on 2006-01-02
Post your /etc/fstab file here.

---

### Post by Thunk on 2006-01-02
Can you see the 120 HD with Gparted?

---

### Post by s_spiff on 2006-01-02
Umm, dunnot about Gparted, will have to check it out. Have to install it first. AS for that fstab stuff here you go :
 
 # /etc/fstab: static file system information.
 #
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
 
 
 
 I have a 120GB HDD [ Master ] , 80GB [ Slave ] , Sony CD Writer, Sony DVD Writer and a Floppy Drive (3.5')

---

### Post by Suger on 2006-01-02
try

sudo mount /dev/hda1 /mnt

---

### Post by s_spiff on 2006-01-02
[quote=Suger]try

sudo mount /dev/hda1 /mnt[/quote]

Well it worked, but it only mounted my C partition  of the 120 gb hdd, how do I mount the other 4 partitions? I tried sudo mount /dev/hda2 /mnt... but it says, you must specify the partition type or something like that. All the partitions can be seen on GPartition.

---

### Post by s_spiff on 2006-01-02
Can someone tell me how to mount other partitions of a hdd [ master ] considering I'm booting from a slave installed linux?

---

### Post by Gustav on 2006-01-02
it's probably hda5, hda6, hda7, hda8

Try gparted to see the names if these aren't correct.

---

### Post by s_spiff on 2006-01-02
Hey Gustav, that worked/ Thank you Very Much, now I can listen to some music! and watch a few movies. :D

---

### Post by Suger on 2006-01-02
Just don't mount them all at the same time in /mnt

---

