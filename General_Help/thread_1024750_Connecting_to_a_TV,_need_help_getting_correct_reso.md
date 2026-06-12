---
title: "Connecting to a TV, need help getting correct resolution"
date: 2008-12-29
forum: General Help
---

### Post by xJoo Unitx on 2008-12-29
So I'm new to Linux in general, but I'm having trouble hooking my laptop up to my TV and getting the whole 1920x1080 resolution I know the TV has.  I'm also running Vista, and when I boot into that I can display just fine.

I run into a problem when I go into System-> Preferences-> Screen Resolution.  I detect displays, turn on the TV display, turn OFF the laptop display, and the highest resolution is 1640x800 or something like that (I don't remember, and I don't have the TV connected right now)

Another problem, is that when running the highest resolution I can on the TV, the screen flickers non-stop, but still functions.

Any help would be appreciated,
Thanks

and here are my system specs if its useful
Ubuntu 8.10
Intel(R) Core(TM)2 Duo CPU  T7300 @ 2.00GHz
Ram: 2.0 GiB
nvidia GeForce 8400M GS

Also, I have the nvidia 177.80 driver installed

---

### Post by colsandurz on 2008-12-29
can I see your xorg setup?

copy and paste from this
```
sudo gedit /etc/X11/xorg.conf
```

Also, what brand notebook are you using?  Some notebooks(like thinkpads) are able to switch between the display and the vga/dvi port in hardware, which means you don't have to configure anything.

---

### Post by xJoo Unitx on 2008-12-29
> **colsandurz said:**
> can I see your xorg setup?

copy and paste from this
```
sudo gedit /etc/X11/xorg.conf
```

Also, what brand notebook are you using?  Some notebooks(like thinkpads) are able to switch between the display and the vga/dvi port in hardware, which means you don't have to configure anything.

thanks for the help but I just solved it about 2 minutes ago and decided to check my thread.

For anyone else having this problem... (anyone with an nvidia graphics card) and I am going to describe it for anyone who is really new like me :-)

1. I went in to my menu settings, changed nvidia x server settings to launch as root. (System -> Preferences -> Main Menu.  then on the left column, I clicked administration under the system tab, and right clicked on the nvidia icon in the right column.  Under command I added "gksu " in front of the text)

2a. Then I was able to play with all of the monitor settings in nvidia. (System -> Administration -> Nvidia x server settings.  then I opened the menu "x server display configuration" to adjust the settings.)

2b. once you've figured out all of you settings, you have to click "save to x configuration file" at the bottom (and now it will let you since it is being run as root) and then just hit ctrl+alt+backspace and your sign in screen should appear with your new settings active

NOTE: For an external monitor (which is what I was doing), click on the one you want active, and configure it, and select separate x screen, then select the resolutions.  and on the screen you want turned off, configure it as disabled.

---

### Post by adam0416 on 2009-02-04
I wish I understood that re my ati card and my 1080p tv

---

