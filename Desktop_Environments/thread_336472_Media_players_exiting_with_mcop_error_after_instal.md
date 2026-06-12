---
title: "Media players exiting with mcop error after installing kubuntu-desktop in ubuntu"
date: 2007-01-11
forum: Desktop Environments
---

### Post by glabouni on 2007-01-11
Since I've installed kubuntu-desktop package in my ubuntu edgy box, media players all fail to start up with a mcop error. I also multiple other installation inbetween, but I'm mentioning kde cause it's mentioned right before the error msg.

I should also mention that I have no sound as my sound card (Supreme FX audio card featuring ADI 1988B 8-channel High Definition Audio CODEC coming with ASUS Crosshair motherboard) is not detected for some reasons.
Not sure if it's related but I'm running in -noapic mode due to a bug leading to kernel panic if I don't.
As I'm also running beryl, I disabled it and tried again just in case, to no success.

for privacy reason, I replaced user name by <username> and box name by <boxname>

gxine and totem:
```
Creating link /home/<username>/.kde/socket-<boxname>.
can't create mcop directory
```

mplayer:
```
mcop warning: user defined signal handler found for SIG_PIPE, overriding
Creating link /home/<username>/.kde/socket-<boxname>.
can't create mcop directory
```


my hardware is: 
AMD Athlon X2 3800+ EE 65W (AM2)
ASUS Crosshair MotherBoard
CORSAIR TWIN2X2048-6400 - DDR2-800 - 2x 1GB
GIGABYTE GV-NX76T256D-RH (GeForce 7600GT)

---

### Post by glabouni on 2007-01-12
no clues that could at least give me a n idea what to search for ?

---

### Post by glabouni on 2007-01-14
*bump*

---

### Post by glabouni on 2007-01-16
if I open a kde session then close it to open a gnome session, then this bug doesn't show.
it's a workaround, but I hope I won't have to do this each time I wanna use a media player

---

### Post by glabouni on 2007-01-17
after having been through a real hassle to get my sound to half-work, and uninstalling and reinstalling ubuntu-desktop, kubuntu-desktop, xubuntu-desktop a couple times, media players seem to be working. can't tell why or how I did it though.

---

### Post by lurgy on 2007-02-26
I just ran into this problem too - a workaround that worked for me was creating a directory named .mcop in my home directory.  Hope this helps. [-o<

---

