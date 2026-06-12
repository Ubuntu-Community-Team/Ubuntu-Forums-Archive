---
title: "Live CD fails to Load on computer: even with correct bios boot order"
date: 2009-05-03
forum: General Help
---

### Post by rasungod_7 on 2009-05-03
I have an old computer lying around and I am trying to put xubuntu on it.

The computer is an old Compaq Presario 5011CL (5000 series)
Has Windows ME on it (that I plan on getting rid of...)
It has a 1.2GHz AMD processor
256 MB SyncDRAM
80.0GB Hard Drive

I downloaded the xubuntu-9.04-desktop-i386.iso burned it on a cd and for some reason it wont boot.

I double checked that the boot order starts with the CD drive.

I then went back and confirmed that the MD5sum of the .iso is correct. 

So now Im stuck and Google isn't helping, what should I do?

---

### Post by lisati on 2009-05-03
Did you remember to burn the ISO file it as a disk image?
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) has some tips that might be helpful.

---

### Post by DeMus on 2009-05-03
> **rasungod_7 said:**
> I have an old computer lying around and I am trying to put xubuntu on it.

The computer is an old Compaq Presario 5011CL (5000 series)
Has Windows ME on it (that I plan on getting rid of...)
It has a 1.2GHz AMD processor
256 MB SyncDRAM
80.0GB Hard Drive

I downloaded the xubuntu-9.04-desktop-i386.iso burned it on a cd and for some reason it wont boot.

I double checked that the boot order starts with the CD drive.

I then went back and confirmed that the MD5sum of the .iso is correct. 

So now Im stuck and Google isn't helping, what should I do?


Are you sure both the cd as the cd-driver are functioning?
Did you try another cd in that drive and did it boot?
Did you try the cd in another computer and did it boot?

---

### Post by MaxIBoy on 2009-05-03
> **rasungod_7 said:**
> I have an old computer lying around and I am trying to put xubuntu on it.

The computer is an old Compaq Presario 5011CL (5000 series)
Has Windows ME on it (that I plan on getting rid of...)
It has a 1.2GHz AMD processor
256 MB SyncDRAM
80.0GB Hard Drive

I downloaded the xubuntu-9.04-desktop-i386.iso burned it on a cd and for some reason it wont boot.

I double checked that the boot order starts with the CD drive.

I then went back and confirmed that the MD5sum of the .iso is correct. 

So now Im stuck and Google isn't helping, what should I do?
Did you burn the ISO to a folder on the CD, or did you actually burn the ISO to the CD as a disk image?

Put the CD into a Windows computer and "autoplay" it. If you get a popup with options for Wubi and stuff, you did it right.

---

### Post by rasungod_7 on 2009-05-03
I couldn't get the CD/DVD creator to work on my linux machine so I used InfraRecorder on a Windows machine, and I used the burn .iso to disk feature.

I just tried to use the xubuntu live CD on a Dell Inspiron E1705 laptop and it didn't work there either!

I made another live CD of Ubuntu 8.10 the same way and at the same time as the xubuntu live CD and it works on the Dell but not the Compaq...

---

### Post by rasungod_7 on 2009-05-03
Well, I kept toying with it and figures out that it was so old that the drive that I was putting the DVD in was a CD ONLY drive! Ha!

It came with a DVD drive but it was not recognized by the BIOS so after I told the BIOS to search for new devices the Ubuntu live cd worked!!!

I still don't know why the xubuntu live cd isn't working... Any ideas??

---

### Post by MaxIBoy on 2009-05-03
Older computers don't always have this feature, but does your laptop have the ability to boot from a liveUSB? If you have at least a 1 GB flash drive, it will work (but be advised that this involves formatting the flash drive.) 

[http://www.pendrivelinux.com/usb-boot-cd-for-xubuntu-810/](http://www.pendrivelinux.com/usb-boot-cd-for-xubuntu-810/) (The directions say 8.10, but the same process ought to work for 9.04. Just boot up a Linux environment (if you've got an installation, or a fast computer with a live CD) to do this.

You could also just install 8.10 and then run an upgrade.


Finally, a computer that old might not run Ubuntu comfortably. Have you considered something like crunchbang (which is Ubuntu compatible but with a more-lightweight default setup?)

---

