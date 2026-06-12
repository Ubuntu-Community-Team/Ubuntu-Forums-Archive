---
title: "How to safety and completely remove Unity and boot to Gnome Shell by defaul?"
date: 2015-03-16
forum: Desktop Environments
---

### Post by remmas-sido on 2015-03-16
Hello guys 
I have recently installed Gnome Shell Desktop Environment and I would like to use it as my main desktop environment,so do you advice me to completely purge Unity desktop environment or I shouldn't remove it because removing it may affect the system stability?
Thank You

---

### Post by dino99 on 2015-03-16
i'm a gnome-shell user only
so i've purged unity as much i've been able; but some related packages can't be purged as they are linked to some other mandatory ones: unity-greeter, libunity9

the easiest way to purge these packages is to install/use synaptic, and first purge ubuntu-desktop (its only a metapackage listing other packages installed by default)

then to login with gnome-shell, click the cog on the right top of lightdm box, and select gnome-shell

---

### Post by buzzingrobot on 2015-03-16
Remember that Unity will not execute when you use Gnome, so the packages just sit on your drive. (The exceptions are the packages mentioned by 9d9, which are required by a number of other Ubuntu packages, whether or not Unity is present.)

---

### Post by jimmyh1972 on 2015-03-18
you cant completely remove unity in the offical canonical version, if you'll do so you can cause other (major) problems to youre machine
if you don't like unity just choose another ubuntu based distro like xubuntu, linux mint, zorin-os etc... 
[http://distrowatch.com/search.php?basedon=Ubuntu](http://distrowatch.com/search.php?basedon=Ubuntu)

---

