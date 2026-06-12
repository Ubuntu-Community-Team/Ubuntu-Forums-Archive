---
title: "XPS M1710 Nvidia problem"
date: 2009-02-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pistelli on 2009-02-10
I have a M1710 with a NVidia Geforce Go 7950 GTX, running 8.10.

I am pretty sure it's out of date because I can't go higher than a 800X600 resolution and cannot enable the visual effects.  I tried enabled the restricted drivers, but it would get to the splash screen and then go to a black screen that I couldn't get out of, even holding down the keys that at least get you a login to a kernal.  After making other post about all this problem, I finally got back to square one, so I want to try again.

In the Hardware Drivers menu in list:
NVIDIA accelerated graphics driver (version 173)  
NVIDIA accelerated graphics driver (version 96)  
NVIDIA accelerated graphics driver (version 177) Recommended

Last time I enabled 177 I got the black screen.

Looking on the NVIDIA website, it tells me that Go 7950  driver is 175.32

I am also updated to initrd.img-2.6.27-11-generic

What do I need to do to get better resolution and the visual effects?

---

### Post by arms3 on 2009-02-25
Had the same problem, found the latest driver on the nVidia site which fixes the problem (though still crashes occasionally) :

[Link to x86 Driver]("http://us.download.nvidia.com/XFree86/Linux-x86/180.29/NVIDIA-Linux-x86-180.29-pkg1.run")
[Link to x86_64 Driver]("http://us.download.nvidia.com/XFree86/Linux-x86_64/180.29/NVIDIA-Linux-x86_64-180.29-pkg2.run")

Download (relevant driver) and copy into your home directory then press Ctrl + Alt + F2, login, then type:
```
sudo killall gdm
```
```
sudo sh -e ./NVIDIA-Linux-x86-180.29-pkg1.run
```
Or path to the other driver if you installed 64 bit linux.
Then just follow prompts and when the installer finishes
```
sudo reboot
```

Hope that works.

---

### Post by pistelli on 2009-05-29
I know this is an old post, but anyone with that particular XPS or a similar model, the graphics card tends to overheat and will need replacing.  If you having problems, more than likely you gpu is shot.  Hope you still got your warranty.

---

