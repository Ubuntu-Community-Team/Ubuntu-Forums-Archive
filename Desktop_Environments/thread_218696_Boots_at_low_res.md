---
title: "Boots at low res"
date: 2006-07-18
forum: Desktop Environments
---

### Post by z3r0-c0d3r on 2006-07-18
My ubuntu installation used to boot at 1024x768 but now after I reinstalled grub (lost it when i installed xp) it keeps booting at 640x480 and i can't change it back 640x480 is the only option in the screen resolution menu.

Can someone help please?

---

### Post by scxtt on 2006-07-18
you'll need to add your HorizSync and VertRefresh values to /etc/X11/xorg.conf, like this (but w/ the values for your monitor):
```
Section "Monitor"
        Identifier   "Sceptre X20G"
        HorizSync    31.0 - 80.0
        VertRefresh  56.0 - 65.0
        Option      "DPMS"
EndSection
```

---

### Post by Dr. Nick on 2006-07-18
if adding your refresh rate doenst fix it you may need to simply add the res back to your /etc/X11/xorg.conf file like I explain here

[http://www.geocities.com/aebcoat/index.html](http://www.geocities.com/aebcoat/index.html)

---

### Post by scxtt on 2006-07-18
as far as i can tell (especially in VMs), the defined resolutions don't matter so much if the V/H rates are correct - it will 'auto detect' available (correct) resolutions ... but there's not harm in defining one's you know your monitor is capable of ...

---

### Post by z3r0-c0d3r on 2006-07-19
I reconfigured xerver and it works fine now thanks for the help

---

