---
title: "Nvidia 8600GT driver in feisty"
date: 2007-05-06
forum: Desktop Environments
---

### Post by forbmj on 2007-05-06
I install the beta nvidia driver in feisty for my 64bit system, but the system couldn't load the nvidia.ko when booting. 

Who has succeeded installing the driver for 8600GT? on 64 bit system?

Thank you for your help in advance.

---

### Post by temis01 on 2007-05-06
Try that !

go to console mode (quit gdm or kdm)

uninstall nvidia = sudo nvidia-installer --uninstall

install this : sudo apt-get install build-essential linux-source linux-headers-`uname -r` xserver-xorg-dev

reinstall nvidia prop drivers beta ...

Nvidia prop drivers won't complain if build-essential is missing, but it is required to build nvidia kernel module properly during installation

Good luck :)

---

### Post by forbmj on 2007-05-07
I have installed all the dependent debs, and no luck. 

I uninstalled all the nvidia related packages, then installed all the dependent debs to compile the beta drivers downloaded from nvidia website. The installation process is quite smooth and I removed the nvidia module first and then modprobe nvidia and got some errors. 

> **temis01 said:**
> Try that !

go to console mode (quit gdm or kdm)

uninstall nvidia = sudo nvidia-installer --uninstall

install this : sudo apt-get install build-essential linux-source linux-headers-`uname -r` xserver-xorg-dev

reinstall nvidia prop drivers beta ...

Nvidia prop drivers won't complain if build-essential is missing, but it is required to build nvidia kernel module properly during installation

Good luck :)

---

### Post by Ekstreme on 2007-05-11
As anyone managed to crack this yet?

---

### Post by uishara on 2007-05-19
I have an 8600gt too which i can't get to work, but i am using 32 bit ubuntu. Restricted-manager informs me that 'your hardware does not require any restricted drivers'. Yeah, right. I think it may be related to a bug that nvidia 6800 and 6600 users are experiencing with restricted-manager. I tried to install nvidia-glx driver on ubuntu 64 bit which I installed on a friends computer that had an nvidia 6600GT, but all I got was a black screen; however, when we wiped the drive and installed 32 bit feisty 3D worked fine.  Have you tried using the 32 bit version?

---

### Post by Rosse on 2007-06-10
I lost 3 days trying different solutions and nothing worked. Each time i rebooted the driver stopped working. Until i found this howto: [http://ubuntuforums.org/showthread.php?p=2791480](http://ubuntuforums.org/showthread.php?p=2791480)
Worked like a charm.:KS

btw. there is a new driver out to (.9) maybe that could solve the problem too?

---

### Post by YaroMan on 2007-08-08
HI I try this [http://www.ubuntuparatodos.org/?q=node/169](http://www.ubuntuparatodos.org/?q=node/169)
and got my card working... but as soon I rebooted system it is stopped working and i had to do all over again... and it is happening after each time i reboot... I need to find some working solution.... as well..

---

### Post by Obor on 2007-08-08
If you guys are still looking for solution, this is how I got it to work few days ago on my new PC (32bit ubuntu), worked on the first try, I guess I got lucky.
[http://www.robdian.co.uk/content/view/56/](http://www.robdian.co.uk/content/view/56/)

---

### Post by iAndrew on 2007-08-09
I hope this works, I'm not a Ubuntu-Savy person.

1st Step:

Stop x-server?:

Ctrl + Alt + F1: Your in terminal.

```
sudo /etc/init.d/gdm stop
``` (STOPS Gnome Display Manager)
[I'm not so sure about KDM, so better luck with someone else]

```
wget -c http://us.download.nvidia.com/XFree86/Linux-x86_64/100.14.11/NVIDIA-Linux-x86_64-100.14.11-pkg2.run && sudo sh NVIDIA-Linux-x86_64-100.14.11-pkg2.run
```

That should be it.

PRESS Ctrl + Alt + F7, to get back gdm.

Or Ctrl + Alt + Backspace, to restart gdm

---

### Post by Kernel_Killer on 2007-09-19
> **Obor said:**
> If you guys are still looking for solution, this is how I got it to work few days ago on my new PC (32bit ubuntu), worked on the first try, I guess I got lucky.
[http://www.robdian.co.uk/content/view/56/](http://www.robdian.co.uk/content/view/56/)

This works great. Worked with my AMD64 Feisty, with the 20-16 kernel, and 100.14.19 NVidia drivers on my XFX 8600GT. One of the 32-bit OpenGL libs never could install, but probably that build of the driver. Still, it ran great, and was easily getting 16000FPS on glxgears.

---

