---
title: "Nvidia drivers on a pen drive"
date: 2007-03-21
forum: Desktop Effects &amp; Customization
---

### Post by cmo220 on 2007-03-21
I have a 4GB pen drive that I am going to use to boot and run ubuntu from.  I was wondering if there was a way to install Nvidia drivers to the pen drive.  Every time I have tried this before the X server wouldn't work and I had to switch back to the nv driver.  Any suggestions would be appreciated.

---

### Post by dfreer on 2007-03-21
Running ubuntu from a pen drive should be the same as running ubuntu from a local hard drive. So your problem shouldn't have anything to do with your pen drive, it's with either your video card, the driver, or how you are installing it.

   What is your video card? Which driver are you using (the one from the repositories, or from nvidia's website), and what version is it? What is your xorg error (it should be found at /var/log/Xorg.0.log)?

---

### Post by cmo220 on 2007-03-21
I'm in the process of installing ubuntu on the drive now so I don't currently have any errors. But, I am using a PNY Geforce 7900GS,  I used to run ubuntu on this computer and never had any problems installing and getting the drivers to work. Thats why I assumed it had something to do with the pen drive.  Once i try it again I'll let you know what the log says.

---

### Post by dfreer on 2007-03-21
Hmmm so you are trying to install the drivers from the live CD onto the pen drive? I would install it to the drive first, then once you boot to it try installing the drivers. Good Luck!

---

### Post by cmo220 on 2007-03-22
That is how I'm trying to do it.

---

