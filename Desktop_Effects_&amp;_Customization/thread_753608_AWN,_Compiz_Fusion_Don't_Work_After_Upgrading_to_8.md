---
title: "AWN, Compiz Fusion Don't Work After Upgrading to 8.04"
date: 2008-04-12
forum: Desktop Effects &amp; Customization
---

### Post by woozyking on 2008-04-12
I know it is not a very good idea for someone like me to upgrade to 8.04, but then I couldn't control my excitement...:(

So here the problem comes, it does not show any error message, just says cannot turn on the effect (of compiz) and for awn, just appeared to flash once and never come out.

Please help:)

---

### Post by lpkizz on 2008-04-14
do you mean The Composite extension is not available is this the messeg you get

---

### Post by Zorael on 2008-04-14
Could you please post the output of entering the following in a terminal?
```
$ compiz --replace
```

---

### Post by lpkizz on 2008-04-14
can you type this in the terminal to install everything compiz just copy and paste everything in one line 

sudo apt-get install xserver-xgl &&  sudo apt-get install compizconfig-settings-manager compiz compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-gnome compiz-plugins libcompizconfig-backend-gconf libcompizconfig0

---

### Post by Eclipse. on 2008-04-14
> **lpkizz said:**
> can you type this in the terminal to install everything compiz just copy and paste everything in one line 

sudo apt-get install xserver-xgl &&  sudo apt-get install compizconfig-settings-manager compiz compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-gnome compiz-plugins libcompizconfig-backend-gconf libcompizconfig0

Wow, chill with the reinstall everything and he doesn't need xgl.

Post the output of: "compiz --replace" 

Also what driver are you using?

Chances are you just need to reinstall your drivers.Its normal, I had to when I upgraded

---

### Post by daniel7860 on 2008-04-14
compiz --replace.............Checking for Xgl: not present. 
Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity

how do i reinstall my driver?

---

### Post by lpkizz on 2008-04-15
> **daniel7860 said:**
> compiz --replace.............Checking for Xgl: not present. 
Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity

how do i reinstall my driver?

will what i said fixes it for me so i can't tell u much

---

### Post by theXfactor9999 on 2008-04-26
I had the same problem as you do. All i did was install the compiz-icon with synaptic then goto Applications/System tools/Compiz fusion icon. when the icon showed up on the top-right side of my screen, i right-clicked on it and reloaded the window-manager. walla! it worked again after setting my compiz pluggins.

---

### Post by Zorael on 2008-04-26
> **daniel7860 said:**
> Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity
Laptops with ati cards have been blacklisted, so you need to force Compiz to ignore that. See the sticky.

---

### Post by echo47 on 2008-05-23
I am having the same problem, only Compiz worked for a little while, maybe half an hour, then stopped.  This is the result of typing compiz --replace:


```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0221 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
aborting and using fallback: /usr/bin/metacity
```

---

