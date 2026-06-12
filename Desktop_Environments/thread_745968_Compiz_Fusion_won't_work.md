---
title: "Compiz Fusion won't work"
date: 2008-04-05
forum: Desktop Environments
---

### Post by prexium01 on 2008-04-05
Hello, I just installed Compiz Fusion, and it's not working... I have the two screens that I can go back and forth from, but that's it, it won't open up the config window, and I don't have the cube. here is what I get when I enter "compiz" into the terminal.

```
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


```

Any help would be appreciated !

---

### Post by Wyrmboy on 2008-04-05
Did you install it from the terminal using this command

sudo apt-get install compizconfig-settings-manager

---

### Post by chewearn on 2008-04-05
> **prexium01 said:**
> Hello, I just installed Compiz Fusion, and it's not working... I have the two screens that I can go back and forth from, but that's it, it won't open up the config window, and I don't have the cube. here is what I get when I enter "compiz" into the terminal.

```
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


```Any help would be appreciated !

You don't have to install compiz in Gutsy; it's already installed by default.  Once you install a graphics driver which can support 3D acceleration, compiz is automatically enabled.

From the compiz terminal output, I would say you are good to go, and compiz is already running (but actually, you don't need to run compiz from the terminal).

Of course, the default compiz set-up is minimal, which is why you see little difference.  To add more effects, you can go to:
System > Preferences > Appearance > Visual Effects > choose "Extra"

If this is not enough, then install compizconfig, as indicated by Wyrmboy.  This will give you a new item System > Preferences > Advanced Desktop Effects Manager

---

