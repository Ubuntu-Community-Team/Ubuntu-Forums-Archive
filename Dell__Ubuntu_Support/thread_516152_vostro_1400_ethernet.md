---
title: "vostro 1400 ethernet"
date: 2007-08-02
forum: Dell  Ubuntu Support
---

### Post by daveyiv on 2007-08-02
Has anyone had any success getting the ethernet port working on any of the vostro lines or the inspiron 1420 or anything? I can't seem to get mine to work in feisty.

---

### Post by LMP900 on 2007-08-02
I had a similar issue and removing the installed tg3 driver and installing a different version did the trick for me. Some relevant links:

[Dell Linux Wiki page detailing the issue]("http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/tg3_driver_does_not_recognize_network_controller")
[Deb file]("http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/tg3_driver_does_not_recognize_network_controller")

Good luck and I hope you can resolve this issue with those links!

---

### Post by daveyiv on 2007-08-02
yeah i have seen that link, but i can't see where it actually tells you how to isntall a new driver. I got the dkms deb and installed that, but thats about as far as that tells what to do

---

### Post by Chandrashekar on 2007-08-10
followed this link and got it working
[http://ubuntuforums.org/showthread.php?t=515275](http://ubuntuforums.org/showthread.php?t=515275)

---

### Post by ayu on 2007-08-12
Hello,
I've read the comments in that link and didn't find anything useful.  I've already installed the tg3-dkms.deb from Dell and it still doesn't see anything in network manager.  I do not want to upgrade to experimental Gutsy right now, although I'm sure that will fix the ethernet.  Any other ideas how to fix or at least start debugging the problem?  I'm running 2.6.20-16-generic right now.  
Btw, the nic lights are orange and yellow when the cable is plugged in.  When unplugged the yellow light remains on.  In Vista, the ethernet works, but the orange light is on.  And ideas about what the lights means?
Thanks!

---

### Post by uber_nerd11 on 2007-09-22
unfortunately when i try to run the deb it complains about a dependency on some program called "gawk".  Does anyone know what it is?  Does anyone know where I can get the deb file for an offline transfer to my laptop?

Side note, does anyone know the deb files needed to upgrade to the latest ubuntu kernel also for an offline install?

Thanks

---

