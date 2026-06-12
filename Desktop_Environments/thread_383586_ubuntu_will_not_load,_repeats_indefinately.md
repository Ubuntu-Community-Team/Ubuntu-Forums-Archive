---
title: "ubuntu will not load, repeats indefinately"
date: 2007-03-13
forum: Desktop Environments
---

### Post by travm on 2007-03-13
Hi, I just installed ubuntu with the alternative method cd using a Text based install.  Everything went well and it appeared to work until it came time to boot into my new system.  Grub properly started gnome and the display manger came up and i put in my username and password set in the install.  Then the panels loaded, and as soon as they loaded the screen went black and the display manager came up again.  I put my username and password in, panels loaded, black screen.  this will cycle for ever.  
I had a similar problem with the live cd but someone suggested i didnt have enough ram (128mb) to use the live cd.

my hardware is
athlon 500mhz
MSI Motherboard with AMD Irongate chipset
128mb pc100 ram
16mb voodoo 3 3500 tv
dlink 10base-T network card

Would really like to use ubuntu, but if it cannot load gnome for me, then I will have to revert back to debian, which i didnt really like due to the complexity of setup, and the fact that desktop environment didnt work as I would expect it to.

---

### Post by Pikestaff on 2007-03-13
You may want to try booting into recovery mode and reconfiguring xorg:

```
dpkg-reconfigure xserver-xorg
```

And selecting the drivers you think you need as well as the optimal screen resolution for your monitor (choose spacebar to select the screen resolution when it asks.)  I'm not sure if that will help or not but I had a similar problem myself and it turned out I had to select different drivers.  Good luck!

---

### Post by travm on 2007-03-13
nope, it still restarts.  I think i need a special driver for my card though.

---

### Post by tech overloaded mom on 2007-03-13
I had this problem yesterday. I found that [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) was very user-friendly and helpful in guiding me through install and this reconfiguring of the x-server as suggested above. Hope this helps.

---

