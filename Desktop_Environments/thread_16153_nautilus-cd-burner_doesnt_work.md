---
title: "nautilus-cd-burner doesnt work"
date: 2005-02-19
forum: Desktop Environments
---

### Post by T31 on 2005-02-19
i cant burn cds :( since i updated open office from hoary, and this is the 2nd time happens to me, since i take any app from hoary repositories, bye bye nautilus-cd-burner and i cant install k3b becouse always corrupt my .ICEauthority file, please..

HEEEEEELP!!!

I dont want to reinstall everything again :P

---

### Post by cwaldbieser on 2005-02-19
Have you tried uninstalling whatever it was that broke the nautilus burner for you and going back to your original versions?

I have had off-and on problems with the nautilus burner myself.  Generally, I use xcdroast as a gui front-end for burning, and I haven't had any problems with it.

You can also try to burn an ISO from the command line if you are adventurous.  I would do something like:
```
sudo cdrecord dev=/dev/hdd driveropts=burnfree /home/carl/ISOs/SUSE-Linux-9.2-LiveCD-KDE.iso
```

To burn a SUSE Live CD in the ISOs folder of my home folder to my CD-Writer (/dev/hdd).  You could just substitute the ISO path and device name in for yourself if you have the cdrecord program installed.

Probably not exactly what you want, but it might suit your purposes.

---

### Post by Qdlaty on 2005-02-19
Hi!
I don't like nautilus-cd-burner but as far as I remember to get K3b working you can not run it as root but with sudo.
Try it.

---

