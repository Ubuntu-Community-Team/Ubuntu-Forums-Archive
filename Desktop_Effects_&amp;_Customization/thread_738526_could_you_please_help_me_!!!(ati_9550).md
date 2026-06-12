---
title: "could you please help me !!!(ati 9550)"
date: 2008-03-28
forum: Desktop Effects &amp; Customization
---

### Post by ahmet on 2008-03-28
here is my problem how can i solve this i try everything on this forum but i cant.!!!


root@Xipetotec:~# SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
Blacklisted PCIID '1002:4153' found 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: No composite extension

(gtk-window-decorator:5919): Gdk-WARNING **: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(gtk-window-decorator:5919): Gdk-WARNING **: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x2e00054 specified for 0x2e00436 (Bullets an).

---

### Post by wobbiebobbie on 2008-03-28
thing would be alot  easer if you would please tell us your speck of your machine and your problem thanks

---

### Post by ahmet on 2008-03-28
specs :

ubuntu 7.10 all updates working 
ati 9550 graphic card
1 gb memory
amd xp 2000+ cpu
240 gb hdd
vs...

i just install it 2 days ago and yesterday i made all of the settings and drivers and they just working well and i can see the visaul effects very good. but today i reboot my machine and than ubuntu cannot find my graphic card and monitor. i try to reinstall and i remove old drivers and reboot than i installed it again but it cannot work. i ve reading all of the posts about this problem and i try everything but it just wouldnt work please help me about.

---

### Post by Ub1476 on 2008-03-28
Are you using the drivers from Restricted Driver Manager? If so, you have to install XGL:

```
sudo apt-get install xserver-xgl
```

Then logout and in for the changes to take effect.

If you are currently using no driver, except for the default arriving with Ubuntu, I suggest you download [Envy]("http://www.albertomilone.com/nvidia_scripts1.html"), which can fetch the latest ATI drivers and configure them for you.

---

