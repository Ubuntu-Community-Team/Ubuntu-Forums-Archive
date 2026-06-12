---
title: "i wiped my hard drive"
date: 2006-08-19
forum: Desktop Environments
---

### Post by matsiacc on 2006-08-19
i wiped my hard drive. and then i made a primary dos partion. 

Then,i tried to install the cd ubuntu 6.06 twice. but everytime i boot my computer, it says operating systems not found. i thought i could boot my computer from the cd burned.

if anyone could help me, i would appreciate it.


mat

---

### Post by meng on 2006-08-19
Is the BIOS set to boot from the CD-ROM? Enter the BIOS setup to check. This may be by pressing the F1, F2, del or esc key at startup. There may be a message telling you which of these keys is correct.

---

### Post by CameronCalver on 2006-08-19
is it possible to install ubuntu from dos?

---

### Post by cptnapalm on 2006-08-19
I seriously doubt it.

Best bet is to set the BIOS to boot from the CD drive.  When the desktop pops up, you can double click the Install icon.  If Ubuntu is going to be the ONLY operating system, then just using the defaults should work fine.

---

### Post by matsiacc on 2006-08-20
i set the BIOS to boot from the CD Drive but it says "operating systems not found" everytime that i boot it from the CD. so i don't know what to do. is it possible that i did not burn well the CD? 
I downloaded and burned two times ubuntu

---

### Post by randell6564 on 2006-08-20
> **matsiacc said:**
> i set the BIOS to boot from the CD Drive but it says "operating systems not found" everytime that i boot it from the CD. so i don't know what to do. is it possible that i did not burn well the CD? 
I downloaded and burned two times ubuntu

Hi!  First.,is what you are trying to install an Iso image?  I've known about some people thinking that they need to extract the iso before installing.

Second.,could it be possible that you have no MBR?  Go into DOS and do a fdisk /mbr (i think thats the correct sytax) and try again.

OH and if none of that works, then JUST for the hell of it, give your drive a file system then try the install again!!

---

### Post by matsiacc on 2006-08-21
> **randell6564 said:**
> Hi!  First.,is what you are trying to install an Iso image?  I've known about some people thinking that they need to extract the iso before installing.

Second.,could it be possible that you have no MBR?  Go into DOS and do a fdisk /mbr (i think thats the correct sytax) and try again.

OH and if none of that works, then JUST for the hell of it, give your drive a file system then try the install again!!

i'm not very sharp on this
how do i extract the iso before installing?

---

### Post by Ramses de Norre on 2006-08-21
Burn it with an option like "burn image" or "burn iso", just burning the file to the disc wont work..

---

### Post by wpshooter on 2006-08-21
You do NOT extract before installing.

The Ubuntu O/S will be installed from the ISO image on your CD.

Are you downloading and burning the DESKTOP cd or the ALTERNATE cd ?

---

### Post by randell6564 on 2006-08-21
> **matsiacc said:**
> i'm not very sharp on this
how do i extract the iso before installing?

Sorry, I guess I was not clear.  You do NOT want to extract the iso.  What program are you using to burn it?  Whatever program it is, you want to use something that makes a reference to iso, or image as Ramses said.  Burn it as slow as you can.

---

### Post by akshaysrinivasan on 2006-08-21
Hmm you mean to say that the live cd isn't working?probably you have burned the cd in a wraong way or downloaded the alternate cd.

---

### Post by randell6564 on 2006-08-21
> **akshaysrinivasan said:**
> Hmm you mean to say that the live cd isn't working?probably you have burned the cd in a wraong way or downloaded the alternate cd.

The alternate cd is actually more stable than the live cd.

---

### Post by matsiacc on 2006-08-21
> **wpshooter said:**
> You do NOT extract before installing.

The Ubuntu O/S will be installed from the ISO image on your CD.

Are you downloading and burning the DESKTOP cd or the ALTERNATE cd ?

i am downloading and burning the desktop cd. 
so, the iso image is bootable right?

thanks

---

### Post by randell6564 on 2006-08-21
> **matsiacc said:**
> i am downloading and burning the desktop cd. 
so, the iso image is bootable right?

thanks

Correct!  But, the alternate cd is more stable. I would advise you to try it since you are having trouble with the live cd.

---

