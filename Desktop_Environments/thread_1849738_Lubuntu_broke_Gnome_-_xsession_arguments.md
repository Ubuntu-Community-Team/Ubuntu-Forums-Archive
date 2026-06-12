---
title: "Lubuntu broke Gnome - xsession arguments"
date: 2011-09-25
forum: Desktop Environments
---

### Post by sam_uk on 2011-09-25
I did a fresh Natty install on this hardware [http://pastebin.ca/2082686](http://pastebin.ca/2082686)

I then installed lubuntu-desktop and dependencies just to give it a try.

Now I cannot log into gnome, it gives an error something like: "too many xserver?/xsesson? arguments (2)" after the gdm login screen.

I want to use gnome! I tried apt-get --purge remove lubuntu-desktop, but the xserver message persists, and I end up completely locked out of the machine, and have to re-install lubuntu-desktop from the command line in order to get a GUI back.

Help!


Thanks

Sam

---

### Post by sam_uk on 2011-09-25
from irc:

if it's anything like a more 'vanilla' system, the solution lies in your ~/.xinitrc
* SLPAN (~slp@109.58.123.237.bredband.tre.se) has joined #lubuntu
<kaja> sam_: basically there's an artifact in your gdm config telling it to start into your old DE AND LXDE

---

### Post by sam_uk on 2011-09-25
So knowing it was a gdm problem I looked around for an alternative to gdm.

I did apt-get install xdm

Which threw up a blue configuration window showing that ldm was my default one.

I just changed the ldm to gdm and rebooted..

Now back in Gnome and happy..

---

### Post by amjjawad on 2011-09-27
Hi,

Why not install Lubuntu on a new partition instead of installing lubuntu-desktop on top of your Ubuntu installation?

---

### Post by phillw on 2011-09-27
Hi,

the current recommended way of adding lubuntu to an existing installation is via [upgrade to Lubuntu](https://help.ubuntu.com/community/Lubuntu/Documentation/UpgradeToLubuntu). That section also includes additional notes on having 2 sets of apps available and tidying up things.

With the new build of 11.10 system, this will quite likely change as we're depreciating the 'no-recommeds install' from 11.10, but the instructions do work for all current releases.

Regards,

Phill.

---

### Post by amjjawad on 2011-09-28
> **sam_uk said:**
> So knowing it was a gdm problem I looked around for an alternative to gdm.

I did apt-get install xdm

Which threw up a blue configuration window showing that ldm was my default one.

I just changed the ldm to gdm and rebooted..

Now back in Gnome and happy..

Is your problem solved or not yet?
If it's solved, please mark this thread as SOLVED :)


[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=7263[/IMG]

---

