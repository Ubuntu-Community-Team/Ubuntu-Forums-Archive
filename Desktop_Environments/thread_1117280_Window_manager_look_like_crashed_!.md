---
title: "Window manager look like crashed !"
date: 2009-04-05
forum: Desktop Environments
---

### Post by Fwé on 2009-04-05
Hi to the ubuntu community ;)

I expose my problem : 

I wanted to upgrade Ubuntu 8.04 => 8.10 with the update manager... nothing crazy ! 
When the installation done, the restart was ... not what I was expecting !!

The window manager is unavailable, you have not any top bar on your windows to close them or manage them... and you can only open windows one by one !!!

If any body knows any thing ....

I continue searching while that time...

Thanks ;)

---

### Post by gettinoriginal on 2009-04-06
Do F11 twice to regain your top window bar.  I do not understand what you are meaning by opening windows one by one.  Welcome to Ubuntu  :p

---

### Post by Fwé on 2009-04-06
Hi,

Oh no i think it is a little worse !! 

This problem comes just a reboot after the Ubuntu update from 8.04 to 8.10.... I had a few errors, but nothing critical... 

I have no more ways to manage windows than the file, edition.. bar. There's nothing up, cannot move or reduce windows !

I tried to create another user with the same properties : the environment loads, and the background image is covered by brown, not
any icons, no window management at all !! just - Application System - bar is present... 

If it can help you understanding my problem : 
when i choose some gnome-apps to manage preferences about interface and all that stuff, i have a message saying : 
[B]Unable to start the preference application for your window manager.
The window manager "unknown" have not registered any configuration tool.[/B] ( i translate from french...)

Thanks !!!!!!!

---

### Post by Fwé on 2009-04-07
any idea ???? 
I tried reinstalling the gnome-art package... nothing new... but some elements were indicated as desactivated...

---

### Post by Fwé on 2009-04-07
up

---

### Post by gettinoriginal on 2009-04-07
It depends on which window manager you want to use.  If you are running compiz, then in terminal:
```
compiz --replace
```
If you are using metacity, then in terminal:
```
metacity --replace
```

---

### Post by Fwé on 2009-04-07
I tried these two commands because i switch between the interfaces (some times compiz has some bugs with Ati cards... )
> **metacity --replace**
Checking for Xgl: not present.
Detected PCI ID for VGA:
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present.
aborting and using fallback: /usr/bin/metacity
**Segmentation fault**
> **compiz --replace**
**Segmentation fault**

I tried to reinstall them via apt-get... nothing new ](*,)

---

### Post by Fwé on 2009-04-08
up

---

### Post by gettinoriginal on 2009-04-08
System Restore
Reboot > during grub splash, hit escape > Recovery mode > Enter (let finish)
Repair Broken Packages > Enter (if it asks about updates hit N) (let finish)
Try to fix X server > Enter (Let finish)
Resume normal Boot > Enter

---

### Post by Fwé on 2009-04-08
Hi ;)

I'm going to try this... 

I hope it will work !!!

thanks again ;)

---

### Post by Fwé on 2009-04-08
I've done the system restore you adviced me....
still nothing... :-s

---

### Post by Fwé on 2009-04-08
up

---

### Post by Fwé on 2009-04-11
Nothing new, I tried to install KDE, in order to have a operational graphical interface on the system, it runs without difficulty... 
I have uninstalled gnome via** apt-get remove gnome**, then reboot, then reinstall it, still the same problem....
Thanks for your ideas ;)

I don't know if it can help you, but on the gnome desktop, one of the symptoms I've not described is the absence of icons in Application and System menus.. The mouse is set to high speed, and if you turn it a little slower, it goes slower than everything !! and I can't turn it to normal settings, like an impossibility to write configuration files or something like that....

---

### Post by Ratscallion on 2009-04-11
Seeing as you upgraded via the Update Manager, may I suggest (unless you don't have any other OS on another partition of your HD) that you backup your home files (in recovery/terminal Control+Alt+F1) to another partition/external HD and then uninstall Ubuntu, and re-install from a fresh Intrepid/Jaunty iso either from disk or from within Windows.

---

