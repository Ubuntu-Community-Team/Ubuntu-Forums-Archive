---
title: "No window borders with compiz"
date: 2009-01-18
forum: General Help
---

### Post by eedaan on 2009-01-18
Hello everybody,

Whenever I try to start compiz, either through terminal or through the appearance menu, all the effects work, but my window borders disappear. The command line output is:

$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

My xorg.conf is attached.

My graphics card is an nVidia 7900 GS, using the version 180 driver.
I'm running 8.10 on AMD 64.

It would seem to me that Xgl is causing the problem, but in synaptic the xserver-xgl package is dead. Does anybody have any idea what's causing this, or even a fix for it?

Thanks in advance :)

Daan

---

### Post by mike2357 on 2009-01-18
Do you have an older nVidia card?

---

### Post by eedaan on 2009-01-18
> **mike2357 said:**
> Do you have an older nVidia card?

A 7900 GS as I later editted, I wouldn't say it's old.

---

### Post by Jeeeep on 2009-01-18
Do you have Window Borders enabled?

If you have CCSM, open it and make sure "Window Decorations" is checked. If you don't have it, use apt-get compizconfig-settings-manager.

---

### Post by steveneddy on 2009-01-18
You might also like to use

Compiz Fusion Icon

for easy access to settings like window borders.

```
sudo apt-get install fusion-icon
```

---

### Post by eedaan on 2009-01-18
> **Jeeeep said:**
> Do you have Window Borders enabled?

If you have CCSM, open it and make sure "Window Decorations" is checked. If you don't have it, use apt-get compizconfig-settings-manager.

Yes I have, and Window decorations was enabled, even re-enabling it didn't help..

---

### Post by eedaan on 2009-01-18
Right, after a little chat with a friend of mine I managed to fix the problem.

In compiz config under the tab of window decoration there was nothing in the "command" bar. So I added /usr/bin/compiz-decorator to that bar, and voila it works!

Screenshot attached for people with the same problem (login needed if you want to be able to view it).

---

### Post by phantom3113 on 2009-01-19
> **eedaan said:**
> Right, after a little chat with a friend of mine I managed to fix the problem.

In compiz config under the tab of window decoration there was nothing in the "command" bar. So I added /usr/bin/compiz-decorator to that bar, and voila it works!

Screenshot attached for people with the same problem (login needed if you want to be able to view it).

To add a tiny morsel to this, if you recently got emerald and would like to use that as your window decorator instead, replace that command with "emerald --replace". Of course, if you have fusion icon, just select emerald under "select window decorator" :P

---

