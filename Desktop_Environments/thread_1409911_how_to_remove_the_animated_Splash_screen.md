---
title: "how to remove the animated Splash screen?"
date: 2010-02-18
forum: Desktop Environments
---

### Post by -glow- on 2010-02-18
Hi there,

im trying to remove the animated splash screen which pops up during the login...i mean those flying dots which circle around a common center.

is there anyway to remove it?

---

### Post by -glow- on 2010-02-18
what happens if i deinstall GDM?

would the bootprocess stop in the console?
can i then just login and type startx?


dont want to mess everything up :/

---

### Post by Hero of Time on 2010-02-18
I think you're referring to a login splash you can set in Gnome settings. I don't know exactly where it is, because I don't use Gnome, but on Xfce4, there is a special setting for it that allows you to use an animation, picture or nothing to show when it's loading your session.
So, check around in the preferences menu and your session editor, maybe you see it there. It has nothing to do with GDM, it's a gnome thing itself.

---

### Post by -glow- on 2010-02-18
perfect im using xfce4 too :)

but i think we're talking about two different things.

there are two animation one is pretty easy controllable through the menu
but the other animation starts before the login screen and right afterwards... thats the one i want to erase the other one is already gone

---

### Post by Hero of Time on 2010-02-18
You mean the one at boot, before you can enter your username and password, right? That is usplash. You can remove it by editing your Grub options. For Grub legacy, edit /boot/grub/menu.lst and search for 'default_options'. It notes 'quiet splash'. Remove the 'splash' part, then run update-grub as root and all current entries should be changed to not show the splash screen.

For Grub2, that's default in Karmic and above, edit /etc/defaults/grub and look for GRUB_CMDLINE_LINUX. Remove the 'splash' part there and run update-grub as root.

---

### Post by -glow- on 2010-02-18
na, its not the bootscreen im talking about.

im talking about this one here more or less:

[http://linuxundich.de/de/ubuntu/human-swarm-xsplash-fur-ubuntu-karmic/](http://linuxundich.de/de/ubuntu/human-swarm-xsplash-fur-ubuntu-karmic/)


its called xsplash...i deleted the xsplash packet but i still have one...the animation is gone the picture stays :/

---

### Post by Hero of Time on 2010-02-18
Well, I don't use GDM, don't have xsplash installed, or any other fancy stuff. Maybe it is GDM that is doing this. You can install LXDM from the Lucid repo manually (download it from [http://packages.ubuntu.com/lucid/lxdm](http://packages.ubuntu.com/lucid/lxdm)) to replace GDM. Maybe that fixes your problem.

---

### Post by -glow- on 2010-02-18
jap its definitely GDMs fault.

i really dont understand why they are doing this on xubuntu...i want xfce because it is/was light and simple...
xfce looks more and more like gnome :/
Ofcourse the gdm problem isnt xfces fault but it goes all in the same direction ...

actually a console login would be sufficient for me... im going to remove the whole gdm stuff

 i deinstalled gdm
modified the /etc/X11/default-display-manager so booting goes directly to the console.

works like a charm :)

---

### Post by Hero of Time on 2010-02-18
Xfce4 is still lightweight, only the Ubuntu devs add a lot of Gnome junk to it that makes it a lot heavier than it should be. Just take a look at installed packages with the name 'gnome' or dependencies to gnome packages. You will find a LOT of them.

I install my systems using Expert mode of the Alternative installer and skip the 'additional packages' install step, so I end up with just the bare minimum for Ubuntu. I install the rest manually, ending up with just what I want and need without all the bloat that comes with a standard installation.

---

### Post by azertyh on 2010-02-18
hi
try it : ```
sudo mv /usr/bin/xsplash /usr/bin/xsplash.disabled
```

---

### Post by Hero of Time on 2010-02-18
> **azertyh said:**
> hi
try it : ```
sudo mv /usr/bin/xsplash /usr/bin/xsplash.disabled
```
When you remove xsplash, that program should be removed too, right? It would be ridiculous if it stayed behind after a remove.

---

### Post by azertyh on 2010-02-18
xplash is not removed, it's always there but with another name. if you want to "ré-install" it :

```
sudo mv /usr/bin/xsplash.disabled /usr/bin/xsplash
```

---

