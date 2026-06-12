---
title: "can the screen saver be configured non-trivially?"
date: 2007-10-14
forum: Desktop Effects &amp; Customization
---

### Post by rybu on 2007-10-14
We have a very limited ability in gnome to configure the screensaver, just the System -> Preferences -> Screensaver options.  Is there any way to configure the screensaver in more detail?  For example, KDE has essentially the same screensaver but in it, one can configure every individual screensaver in detail.   How do we get that kind of functionality?

---

### Post by 5-HT on 2007-10-14
Not with gnome-screensaver (that's supposed to be a feature:-k).
Using xscreensaver instead will do the trick.
cheers,

---

### Post by rybu on 2007-10-14
> **5-HT said:**
> Not with gnome-screensaver (that's supposed to be a feature:-k).
Using xscreensaver instead will do the trick.
cheers,

A feature of the Soviet Union was they had no choices on their election ballots.  I don't see how either feature is in any way desireable.  Having a screensaver where every aspect is configured poorly is a sad waste of resources. 

So a question for noobs.  How do I disable the Gnome screen saver and enable the xscreensaver?

---

### Post by 5-HT on 2007-10-14
Removing gnome-screensaver and installing xscreensaver alone should do the trick. If you get dependency issues with gnome-screensaver you could either let ubuntu-desktop go along with it or make /usr/bin/gnome-screensaver non executable (sudo chmod u-x /usr/bin/gnome-screensaver). If xscreensaver isn't taking over, adding it to your session startup programs will take care of it

---

### Post by rybu on 2007-10-14
> **5-HT said:**
> Removing gnome-screensaver and installing xscreensaver alone should do the trick. If you get dependency issues with gnome-screensaver you could either let ubuntu-desktop go along with it or make /usr/bin/gnome-screensaver non executable (sudo chmod u-x /usr/bin/gnome-screensaver). If xscreensaver isn't taking over, adding it to your session startup programs will take care of it

Thanks, xscreensaver seems to be running well.  There's loads of screen savers that are "greyed out" on the xscreensaver menu, which it says are not installed.  Is there a particular reason for that?  Are these screensavers available but not "supported" by Ubuntu?

---

### Post by FuturePilot on 2007-10-14
```
sudo apt-get install xscreensaver-data-extra xscreensaver-gl xscreensaver-gl-extra
```
That should give you a whole bunch of extra sceensavers:)

---

### Post by cliffhanger407 on 2007-10-17
This is in the same vein as the problems here... I followed both this and [http://ubuntuforums.org/showthread.php?t=195557](http://ubuntuforums.org/showthread.php?t=195557) while running feisty a while back, everything worked fine. Being the early adopter that I am, I'm now running the RC for Gusty. Needless to say, I wanted to upgrade to xscreensaver. I've tried doing several things, and nothing seems to work.
```
sudo apt-get install xscreensaver
```
Says that package "xscreensaver is not available". I'm online, and it recognizes that xscreensaver is referenced by xscreensaver-data. If I try running xscreensaver from bash, it says xscreensaver is not a recognized command (which obviously means it's not installed).

Sorry for the bit of the hijack, but where should I go from here? I've run made sure that apt-get is updated, It's definitely running as root, and I'm very confused. :confused:

Help is very much appreciated. This is the first time I haven't been able to solve my problem by just searching, so I'm pooling the wisdom that's out there on this one.

Possibly relevant extra info:
Dell e1405
Intel 945g chipset
Gusty 7.10
Gnome 2.20.0

(I'd like to just go through a package, but I suppose I could just get a tar.gz file for it...)

**EDIT**
I solved my problem, it was with apt-get, not with anything else.

---

### Post by Krydahl on 2007-12-03
Having replaced the woeful gnome-screen saver with xscreensaver (which worked fine in fiesty), in Gusty I'm now seeing Xorg hit 70% cpu occupancy when the screensaver starts. Not ideal!

Anyone any idea how to sort this?

---

