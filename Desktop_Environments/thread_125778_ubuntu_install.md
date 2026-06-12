---
title: "ubuntu install"
date: 2006-02-04
forum: Desktop Environments
---

### Post by plecostos on 2006-02-04
to start off with i'm pretty much a linux noob :roll: 

I recently wanted to install ubuntu 5.10 on my system, after installing and using the standard formatting, removing the cd, restart, the ubuntu logo comes up...
then after uncompressing linux...
an error comes up saying "/dev/hdf1 does not exist dropping to shell"

---

### Post by plecostos on 2006-02-04
also, all hardware during the install is recognized and its a single hard drive system.

---

### Post by magomago on 2006-02-04
if its a one drive system shouldn't /dev/hd**f**1 be /dev/hda**1**?  

i'm no expert, and probably more green than i should be but check your fstab.

gedit /etc/fstab

does it list your hdd as /dev/hdf1? I'm assuming that with the cd you can somehow still look at your drive.  That just seems weidr

---

### Post by taurus on 2006-02-04
Yes, it has to be a typo in /etc/fstab for sure unless you have 6 HDs on your machine!!!  Now it's a good time to use the LiveCD and make the correction in your /etc/fstab and reboot without the CD in the drive...

---

### Post by plecostos on 2006-02-04
i think the hdf1 may have been because this system *had* three harddrives in it, and two optical, in various configurations, but i'm really not sure how that could affect anything...:confused: 

i'm installing ubuntu with one drive in the system, and one drive when that error comes up. I have a very odd add in pci ata/133 controller that might be causing the problem... i'm gonna take it out, and detach everything cept a cd drive and the hard drive and see if i can get a working install.

then i'll try the live cd probably tomorrow if that doens't work...

---

### Post by magomago on 2006-02-06
Yeah try that.  

Although I have a generic promise controller that my Linux HDD is attached too (Windows and Linux each have their own harddrives...my linux is /dev/hde2 or something b/c the second drive actually is partitioned for storage at the same time) and not experiencing problems.

But yeah try it with it taken out.

---

