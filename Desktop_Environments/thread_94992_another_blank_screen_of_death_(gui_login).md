---
title: "another blank screen of death (gui login)"
date: 2005-11-25
forum: Desktop Environments
---

### Post by kwm on 2005-11-25
my problem is nearly identical to this thread: [http://www.ubuntuforums.org/showthread.php?t=86972&highlight=gnome+login](http://www.ubuntuforums.org/showthread.php?t=86972&highlight=gnome+login)

simply put, once I make an attempt to login, everything seems to freeze up and I am left with a blank brown screen.  the keyboard goes dead, so I can not switch terminals via ctrl+alt+Fx, but my mouse cursor still responds.  I can also trigger the lockup by going into session options and choosing a different option than 'Last'.  I get no x server errors in my log files, and I have no clue what to do.  this is a fresh install of Ubuntu (also my first, btw).  I have tried every piece of advice given in the above mentioned thread.  some system specs:

amd athlon xp 3000
nvidia geforce 6200 with nv driver
1 gig corsair ram
dell FPW 20.5 inch

I seem to relate to the above thread in both architecture and video card.  I'm assuming one of these is the cause of our problems.  ANY help is much appreciated.

---

### Post by tseliot on 2005-11-26
Try this quick fix:
Turn on your computer and keep pressing ESC until the GRUB menu shows up.

Select "Recovery Mode"

It will boot to the command line

then try this:

Type:

```
sudo nano /etc/X11/xorg.conf
```

Find the section Device and make sure the word I put in red is &#8220;vesa&#8221;:

```
Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "[COLOR="Red"]vesa[/COLOR]"
BusID "PCI:1:0:0"
```


```
CTRL+O to save (yes, use the same name and overwrite the file)
CTRL+X to exit
```

Then type:
```
sudo startx
```

And the Graphical interface should start.

Then, [COLOR="Red"]if you can enter the Graphical interface[/COLOR], you might want to install Nvidia proprietary drivers (for 3D acceleration and better performance). Here's my guide: [HOWTO: Latest NVIDIA drivers]("http://ubuntuforums.org/showthread.php?t=75074")

---

