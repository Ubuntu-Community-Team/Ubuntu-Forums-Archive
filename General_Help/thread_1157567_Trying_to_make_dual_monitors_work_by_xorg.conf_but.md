---
title: "Trying to make dual monitors work by xorg.conf but (permission?)"
date: 2009-05-12
forum: General Help
---

### Post by DJSchmidty on 2009-05-12
Just installed Jaunty on a home brew computer, running an 8400 gts with dual monitors...

When I first installed, it gave me dual monitors right away, which was weird, but what ever...

Anyways, went into displays, enabled dualview, and copied the preview of the xorg.conf, and opened gedit and tried to save the file, but for some reason it says I don't have permission to save this file???? wtf.

Then, I made a NEW file, saved it as xorg.conf, and tried to copy it over, but still gave me a permission error..

A little help?
Thanx

---

### Post by BslBryan on 2009-05-12
Hello, DJSchmidty. :-)

Are you root?

---

### Post by DJSchmidty on 2009-05-12
Hi there..

No, i'm logged in as 'blackbox' don't know how to login as root (still learning ubuntu)

---

### Post by BslBryan on 2009-05-12
Ah.  Just add 
```
gksudo
```
or
```
sudo
```

before your code.  So, to modify xorg.conf,
```
gksudo gedit /etc/X11/xorg.conf
```

:-)

---

### Post by DJSchmidty on 2009-05-13
Thanx for the quick reply, but now I have a huge problem...

I would be freaking out if this was an install with a whole bunch of stuff on it, luckily this is on a plain jane fresh hard drive, but heres what happens::

K, so I install the latest nvidea driver (1.8 i think) and the screen on the right looks great, everything looks clean, and the correct resolution.  I then go into nvidea xserver, and enable the left screen with twinview, and setup the monitors in the xserver as they are in front of me..  I goto save the configuration (and obviously get told that I don't have permission) so I look at the preview of the xorg.conf, copy all to clipboard, do the gedit with root like you said (a blank gedit screen comes up by the way) and input all of the xorg.conf info from the preview.  Then I save the file over the previous xorg.conf, and restart....

Whoa!! What a mess...

I get to the login splash screen, input user and pass, and when i'm hearing the intro ubuntu theme music, it locks up and freezes, and I have to restart, which never gives me an x screen again, i'm now on my 3rd attempt re-installing 9.04..

Driver? Video card? me? LOL..

Thanx in advance for and help on this one!

---

