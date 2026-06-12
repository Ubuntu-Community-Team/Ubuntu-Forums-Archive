---
title: "Beryl help : /"
date: 2007-05-27
forum: Desktop Effects &amp; Customization
---

### Post by pnx031 on 2007-05-27
I am trying to install Beryl on my Radeon 9800...

I find it impossible to do :/

I followed: [https://help.ubuntu.com/community/Beryl/ATI/Feisty?highlight=%28beryl%29](https://help.ubuntu.com/community/Beryl/ATI/Feisty?highlight=%28beryl%29)

this tutorial, and finished up to restricted drivers instalation... which finished succesffuly and I restarted... but when i typed in the terminal fglrxinfo i got this output:

```
pnx031@pnx031-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

```


I dunno what I am doing wrong... :/

help? ;s

---

### Post by dfreer on 2007-05-27
ati drivers are, at best, a pain to install. 
you currently do not have them installed correctly, that is why it shows mesa under the vendor string.
try using one of the automated scripts mentioned in this forum (envy, automatix2, or whatever), or you can post the output of:
```
cat /etc/X11/xorg.conf | grep -A 5 -B 5 Busid
```

p.s. there should be an eaiser way to grep /etc/X11/xorg.conf but i don't know it :D

---

### Post by pnx031 on 2007-05-28
when i wrote : 

I got this result back: cat /etc/X11/xorg.conf | grep -A 5 -B 5 Busid

```
Section "Device"
        Identifier      "ATI Technologies Inc RV350 NJ [Radeon 9800 XT]"
        Driver          "fglrx"
        Busid           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"

```

and what about the automated scripts? where can i find them?

---

### Post by pnx031 on 2007-05-28
well i tried installing source drivers but when i type fglrxinfo i get :

```

pnx031@pnx031-desktop:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

```

---

### Post by Ub1476 on 2007-05-28
```
 glxinfo | grep direct
```

Use that code in a normal gnome session to check if 3d is enabled.

If it turns out like: direct rendering: yes .. 
.. you can continue install beryl.

---

### Post by pnx031 on 2007-05-28
it returns no :S

any ideas ?
i even installed the driver with envy and still nothing :S

---

### Post by Ub1476 on 2007-05-28
Have you tried to install it through "Restricted Drivers Manager"? If you'll try, uninstall envy first.

---

### Post by dfreer on 2007-05-28
From what I understand of it, when installing ATI drivers the MESA drivers conflict with it, it seems like it's a quickdraw to see which driver the system actually uses. I'll try to find some guides, but what you'll prolly need to look into is blacklisting the MESA driver in the kernel, so that only the official ATI driver is loaded.

---

