---
title: "crap, i lost X"
date: 2006-03-14
forum: Desktop Environments
---

### Post by Daboo on 2006-03-14
I tried to follow this guide for installing XGL/Compiz: [http://www.tectonic.co.za/view.php?id=916](http://www.tectonic.co.za/view.php?id=916)

On reboot, X does not start up correctly. How can I salvage this and get back into gnome? I tried deleting the .Xsession file I created in home, but nothing.

I was just too tempted by eye candy...damnit!

---

### Post by TLE on 2006-03-14
I don't really know what this program do so I don't know where it might make changes. But you could check if your X configuration file is allright.
First make a copy
```
cd (your home drive)
cp /etc/X11/xorg.conf .
```
then make a new xorg.conf
```
sudo dpkg-reconfigure xserver-xorg
```
If you are in doubt of what to answer to the questions just choose the default. If it doesn't help then copy the old one back in its place
```
cd (your home drive)
sudo cp xorg.conf /etc/X11/xorg.conf
```

---

### Post by Daboo on 2006-03-14
I tried it and I got the same error. Here's some detail:

(EE) Unable to find a valid framebuffer device
(EE) NV(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
(EE) Screen(s) found, but none have a usable configuration

Fatal server error: no screen found

---

### Post by Daboo on 2006-03-14
What's more, my network also doesn't work. I tried dhclient and got something about a address/mask length mismatch. I think I'm screwed :/ Luckily I was able to get to my files through XP, but it would be nice if I didn't have to reinstall.

---

### Post by TLE on 2006-03-14
Sorry, can't really help you there. I hope you'll get it up and running.

---

### Post by mlind on 2006-03-14
Does nv driver need a framebuffer module?
if you don't have it on your xorg.conf, try to add it.
if you have it, try to remove it.

see Modules section on xorg.conf
```

Load    "fb"

```


if you're actually have nvidia card, try using nvidia's official drivers instead.
I know that nvidia driver loads its own framebuffer.

---

### Post by mlind on 2006-03-14
what kinda network interface you have?

does *sudo /etc/init.d/network restart* bring it back alive?

---

