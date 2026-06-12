---
title: "sudo apt-get install kernel-image-686 causing problems."
date: 2006-07-07
forum: Desktop Environments
---

### Post by txuk on 2006-07-07
Hi people,

Started using ubuntu a couple of weeks ago after finally finding that there was a linux distro good enough to use as a day to day desktop OS (Have tried many other linux, but have always used them as servers as they never seemed to cut it as a desktop.. (epecially speed wise!)

Anyway, talking of speed, installed drake on toshiba laptop, 1.50ghz Celeron M, 512Mb DDR, ATI Graphics. And it was sweet! got NetworkManager and Network-Manager-Gnome installed for wifi mainly, and got ati drivers (flgrx or whatever they were) and the xgl stuff working perfectly.

However i was then reading that using the 686 kernel would give improvements to the speed of the system instead of using the defualt 'works with anything' kernel that ubuntu installs.

This made sence to me so i did a 'sudo apt-get install kernel-image-686'

Installed fine, restarted..... aaaaannnddd...

Tis crap, XGL is gone, Decent display drivers (the ATI ones) aint being loaded, wifi card (atheros PCI) isnt detected anymore. now im guessing a lot of that was due to those features being kernel modules... and i would need to rebuild the modules for the new kernel??.. so that dosnt really bother me, what DOES bother me is its sooooo much slower than running the 386 kernel.

I mean, am i missing something? is the celeron M such a cut down cpu that is dosnt have all the features 686 asks of a processor?

or have i just missed something really stupid? I heard the support on this forum is great, so if anyone could give me any ideas of howto resolve these problems... 
I know i can always go back to the 386 kernel from grub, but, shouldnt the 686 kernel be faster? would be really great to get it working properly.

Regards,
Tx

---

### Post by FredB on 2006-07-07
I don't know if 686 version is quicker than the old. The problem is that xgl (and so display drivers) are based on the 386 version.

The simpler is to go back to 386 version. And to remember this :

*"It if it is not broken, don't fix it"* :)

---

### Post by txuk on 2006-07-07
Done and Done!

---

