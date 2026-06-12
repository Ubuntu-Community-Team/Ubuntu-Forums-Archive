---
title: "Ubuntu on USB experience"
date: 2009-06-20
forum: General Help
---

### Post by lindberg.bill on 2009-06-20
I have been using puppy on a usb stick for a while and I love it.  I would like to try using other distros on usb sticks as well.  I tried Kbuntu, but it was very slow.  I believe this is due to my older laptop.  
Dell Lattitude D510
Celeron M processor
512 ram
I'm going to try Ubuntu Jaunty next because I had no trouble running this distro on my hard drive.  I know that applications will load slowly and possibly the startup will be slow, but I'm wondering what other troubles might come my way.  I will be using a 4GB Sandisk Cruser with the U3 software removed and disk formatted.  My question is can any one currently booting ubuntu "full installation on usb" relate some of their experience with it.
I'm not asking how to install I already have that figured out.  There are numerous tutorials.

---

### Post by masux594 on 2009-06-20
mmm.. I think that there's no problem [slowness apart].. is only a location, If is possible doing things like this, means that the OS should work correctly anyway =)

Sysc, A

P.s. I have no personal experience about this!

---

### Post by tea for one on 2009-06-20
> **lindberg.bill said:**
>  I will be using a 4GB Sandisk Cruser with the U3 software removed and disk formatted.  My question is can any one currently booting ubuntu "full installation on usb" relate some of their experience with it.
I'm not asking how to install I already have that figured out.  There are numerous tutorials.

I have installed Ubuntu 9.04 on a 4GB Sandisk Cruzer with U3 removed. 
As a "live" USB device, I would estimate that it boots a bit slower than a "live" CD; however, when Ubuntu has loaded, the performance is pretty good. 

I suspect that there are plenty of tips/tricks to speed up the booting process.

Don't forget to include the "persistence" when creating the device.


I forgot to add that I used FAT 32 on the USB stick because you can still read/write to the spare space via Windows XP PC. For example, on the same stick, I use Portable Apps ([http://portableapps.com/](http://portableapps.com/)) if I use a PC where I cannot influence the boot priority.

---

### Post by lindberg.bill on 2009-06-23
OK I have installed the ubuntu 9.04 to the usb stick.  Now I want to be clear that I did not use the live image with persistence or the usb backup drive method.  I simply used the install feature from the live disk to install to the usb drive instead of the hard drive.  I am noticing some performance issues, but as I said before this is an older laptop, so no big deal.  I do want to comment that this is possibly a good way for some one to try this distro with a full install and see how they like it.  I was hoping for some more input from others but that is OK thank you for your comments and good luck with your projects.

---

### Post by BlueCanary9999 on 2009-06-23
I'm interested in installing Ubuntu onto a flash drive.  Can you link me to the tutorials you found?  I haven't been successful in finding any... although I came across this topic.  :D

---

### Post by rushikesh988 on 2009-06-23
> **BlueCanary9999 said:**
> I'm interested in installing Ubuntu onto a flash drive.  Can you link me to the tutorials you found?  I haven't been successful in finding any... although I came across this topic.  :D
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent")  


may be this will help you

---

### Post by Mighty_Joe on 2009-06-24
I run Ubuntu 9.04 off a USB flash drive and am pretty pleased with it. Of course, I have 2GB of RAM so I don't need a swap partition (swap's going to really slow things down on a USB drive).
I used these [install]("http://beastie.cs.ua.edu/cs150/usb-install.html") and [configuration]("http://beastie.cs.ua.edu/cs150/configuration.html") instructions to set it up.
You have two bottlenecks to deal with. You have slow hardware AND you are running off a slow USB drive.  Xubuntu will probably run better, as its window manager is lighter.  Puppy is way stripped down (it's a 100Mb download, compared to Ubuntu's 700Mb).  There are some other light distro's based on Ubuntu, like Crunchbang and Fluxbuntu you may want to try.

---

### Post by rogueleader12345 on 2009-06-24
I've got Jaunty running on a 4 gig as a live USB and it boots up quick, it's persistent, and runs well. You should be good to go, but I do suggest getting a newer laptop, if you can come up with one for cheap. :)

---

### Post by lindberg.bill on 2009-06-24
[http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html)
 
I like this method and I think it is easy and sure to work.  I'm not sure if the live with persistence method is better for any reason or not.

---

### Post by Mighty_Joe on 2009-06-25
> **lindberg.bill said:**
> [http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html)
 
I like this method and I think it is easy and sure to work.  I'm not sure if the live with persistence method is better for any reason or not.

He's just doing a full install to a USB hard drive.  He's added a step to change the drive number in Grub which is unnecessary now because the 9.04 installer configures Grub to use UUID's, which do not change when the boot order is changed.
The instructions I posted tell how to tweak a full install so it avoids hitting the slow USB drive, for example, moving logging to tmpfs.
As for the LiveCD or full install being better, the LiveCD fits on a smaller drive (700Mb vs. 2GB+ for a full install), but the full install is faster because it isn't compressed.

---

### Post by BlueCanary9999 on 2009-06-27
Thanks for the suggestions, guys!

---

