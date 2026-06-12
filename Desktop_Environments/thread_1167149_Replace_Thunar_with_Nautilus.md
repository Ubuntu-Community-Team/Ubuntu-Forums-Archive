---
title: "Replace Thunar with Nautilus"
date: 2009-05-22
forum: Desktop Environments
---

### Post by geokker on 2009-05-22
Yes, you read right. I need the functionality offered by nautilus so I've installed it and use it happily in Xubuntu Jaunty (XFCE4). However, when I boot the PC, Thunar (I think) controls the desktop. I want Nautilus to control the desktop e.g. draw the icons etc. IS there any way I can completely replace Thunar with Nautilus - or would it no longer be XFCE? The Gnome desktop is still too 'heavy' and the compositing isn't as efficient.

Cheers.

---

### Post by kerry_s on 2009-05-22
in xfce4 the desktop is done by xfdesktop, not thunar, thunar does not do desktop icons.

what i would try to do is put> **killall xfdesktop** <in the startup with **nautilus** starting after it.

---

### Post by geokker on 2009-05-23
It works, but then the process 'auto spawns' in a Quake-like manner. I'd have to put 3 or 4 killall entries in which is a bit hacky and lengthens the login process.

---

### Post by kerry_s on 2009-05-23
> **geokker said:**
> It works, but then the process 'auto spawns' in a Quake-like manner. I'd have to put 3 or 4 killall entries in which is a bit hacky and lengthens the login process.

i didn't think it would be that easy. i do have a plan b, but it may screw you later if those programs get up dated, just letting you know.

so plan b, would be to replace xfdesktop with a link to nautilus.

in a terminal:

[B]sudo mv /usr/bin/xfdesktop /usr/bin/xfdesktop-off
sudo ln -s /usr/bin/nautilus /usr/bin/xfdesktop[/B]

that's it, just remove your startup stuff, logout and back in and hopefully it will be using nautilus.

---

### Post by geokker on 2009-05-26
Excellent, works a treat - cheers.

:)

---

### Post by waldir1 on 2011-04-24
works fine but what about desktop and places plugin? have i missed some simple solution, or have i to choose between nautilus without these details, gnome + nautilus or thunar + xfce
/edit I mean that now there is only brown background instead of wallpaper and plugin which shows menu "places" is working only with thunar (on uninstall of thunar it is also uninstalled and while thunar is installed it launches thunar... and i haven't found simillar applet for nautilus, although in gnome it's somehow integrated)

---

### Post by flar on 2011-08-08
Instead of changing symlinks, you could uninstall xfdesktop and add nautilus to your session start up list.  It's been working well for me so far and won't get overwritten during updates.

---

### Post by tivatranquio on 2012-05-20
> **flar said:**
> Instead of changing symlinks, you could uninstall xfdesktop and add nautilus to your session start up list.  It's been working well for me so far and won't get overwritten during updates.

Does this solution works with xfce 4.10 ?

---

### Post by lisati on 2012-05-20
Old thread being put back to sleep. :(

---

