---
title: "Compiz broken"
date: 2009-01-03
forum: General Help
---

### Post by FeistyStyle on 2009-01-03
Bought a new monitor for my ps3 and hooked it up to my laptop with VGA to see how it looked on here also. then I unhooked it and went on with my life but came back later and noticed metacity was being used instead of compiz. terminal shows this

kenneth@kenneth-laptop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 


reinstalling compiz and restarting have not worked

---

### Post by stderr on 2009-01-03
```
sudo dpkg-reconfigure xserver-xorg
``` (and following the prompts) may help tidy up the xorg.conf.

You can back it up first with

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

What video card are you using, and which driver?

---

### Post by FeistyStyle on 2009-01-03
Intel 945gm with the intel driver

reconfiguring Xserver didnt work :(

---

### Post by FeistyStyle on 2009-01-03
ahhhh. I tried reconfiguring a second time and it worked. (dont know why it still crashed after the first time)

appreciate it

---

