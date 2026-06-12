---
title: "usb hard drive unmounted automatically"
date: 2009-05-17
forum: General Help
---

### Post by cedric_libre on 2009-05-17
Hi, 
 I am using Ubuntu 8.04 Hardy Heron on an AMD Athlon 1.2 GHz processor .
 I'd like to save the data on my home partition as I have the impression the hard drive hosting it is going to "die" soon .
 I've bought a USB Sata hard drive of 320 GB and actually the volume of data I'd like to transfer is far lower, around 15 G .
 
 I've formatted two primary partitions on the drive .
 One is ext2 (30 G) and the other one is 260 G with reiser fs .
 I use the following command to save my datas :

 sudo nice -n 19 rsync -P -av --exclude=".*/" /home/cedric/ /mnt/home/cedric/


 Here is the problem :

 A few files get transfered and each time, it ends with I/O error messages and the device file /dev/sdc2 representing the reiserfs partition gets deleted .
 Listing /dev directory, it appears that the two partitions are renamed as /dev/sdd1 and /dev/sdd2 .

 I've tried to mount /dev/sdd2 instead of /dev/sdc2, but the same scenario repeats : I/O errors, /dev/sdd2 deleted and creation of /dev/sde2, etc...

 What do you think about this ?

 Thanks a lot for your help,

 Cédric

---

### Post by cedric_libre on 2009-05-17
Hi,
 I posted this message in hardware and that was a mistake as the usb HD is recongnized , so I moved it here .

Here is my problem :

 I am using Ubuntu 8.04 Hardy Heron on an AMD Athlon 1.2 GHz processor .
I'd like to save the data on my home partition as I have the impression the hard drive hosting it is going to "die" soon .
I've bought a USB Sata hard drive of 320 GB and actually the volume of data I'd like to transfer is far lower, around 15 G .

I've formatted two primary partitions on the drive .
One is ext2 (30 G) and the other one is 260 G with reiser fs .
I use the following command to save my datas :

sudo nice -n 19 rsync -P -av --exclude=".*/" /home/cedric/ /mnt/home/cedric/

The problem is that a few files (~ 50 % ) get transfered and each time, it ends with I/O error messages and the device file /dev/sdc2 representing the reiserfs partition gets deleted .

Listing /dev directory, it appears that the two partitions are renamed as /dev/sdd1 and /dev/sdd2 .

I've tried to mount /dev/sdd2 instead of /dev/sdc2, but the same scenario repeats : I/O errors, /dev/sdd2 deleted and creation of /dev/sde2, etc...

What do you think about this ?

Thanks a lot for your help,

Cédric

---

### Post by cedric_libre on 2009-05-19
up !

---

### Post by cedric_libre on 2009-05-25
Maybe someone can be interested by the solution .
 My old motherboard is equipped with a 1.1 USB controller.
 Thanks to a PCI to USB 2.0 card it works now perfect!!
 Ciao

---

### Post by hal8000 on 2009-05-25
Thats an interesting solution especially as USB 2.0 devices are backward compatible with USB 1.1, thanks for sharing

Glad you got it working eventually.

---

