---
title: "dapper freezes and becomes unresponsive"
date: 2006-06-19
forum: Desktop Environments
---

### Post by lonelypauly on 2006-06-19
ok, first of all, this dapper release is great...i love it...and im certainly not the complaining type...but this really sucks. im running the 32 bit version on my 64 bit computer.

on a few occassions now...i have noticed that my system will completely lock up after it has been sitting idle for over a few hours.  the past few times this happened was when i came home from work and found my machine was locked up and not responding at all (ctrl alt backspace did nothing)

any ideas?  should i run memtest?

---

### Post by nanotube on 2006-06-20
a few things to check, sequentially:
1. turn off your screensaver
2. switch your video driver to "vesa" in /etc/X11/xorg.conf
3. try running memtest and see if your ram tests out ok

if none of these make the lockups go away... post back here. if one of these does, post back here anyway and let us know ;)

---

### Post by lonelypauly on 2006-06-20
cool, i shut off my screensaver...will run memtest tonite.  how do i switch my driver to "vesa", and what is that, anyway?

im using the latest Nvidia driver for my GF6800...don't remember having problems with breezy.

thanks for the quick response nanotube.

---

### Post by nanotube on 2006-06-20
[QUOTE=lonelypauly]cool, i shut off my screensaver...will run memtest tonite.  how do i switch my driver to "vesa", and what is that, anyway?

im using the latest Nvidia driver for my GF6800...don't remember having problems with breezy.

thanks for the quick response nanotube.[/QUOTE]
to switch your driver to vesa, edit your /etc/X11/xorg.conf, and the line where it says
```
Driver "nvidia"
```
change that to
```
Driver "vesa"
```

(you have to do it as root, with sudo, of course. and have to restart the comp for it to take effect). vesa is just the "lowest features failsafe video driver" basically. :)

but don't bother with it if turning off the screensaver does the trick. so test the first step first, then if it doesn't work go to the second, then if that doesn't work go to the third. you don't want to do all of these at the same time without testing, because then you won't know which one of these actually worked. :)

---

### Post by lonelypauly on 2006-06-21
that is one of the first things i did since i have two monitors...i downloaded the latest nvidia drivers and change the config.  i will double check it.  since i shut off my screen saver, i havent had any problems...i will keep an eye on things and report back if that doesn't fix the problem.

---

