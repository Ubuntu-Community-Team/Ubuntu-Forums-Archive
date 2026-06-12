---
title: "Beryl, Heliodor, Aquamarine... ARGH!"
date: 2007-09-18
forum: Desktop Effects &amp; Customization
---

### Post by hoboken on 2007-09-18
OK, this will hopefully be the thread to whack the final nail in this bug's coffin, namely:

WHERE ARE MY WINDOW DECORATIONS?

*cough*

I'm using beryl now, because compiz was no-go; there are serious compatibility issues between the various packages when installing through apt-get. Anyway, I've managed to bypass the lack of window decorations by switching to Heliodor rather than Emerald as my window decorator, but I'm not really familiar with it. 

Some questions: how do I change the theme? Can it even be done? And, most importantly, why does emerald not work?

I know the problem is not with ME, because:
Hardware - beryl worked perfectly 3~ months ago
Software - I've just done a fresh install of Feisty.


Thoughts?

---

### Post by reacocard on 2007-09-18
> **hoboken said:**
> OK, this will hopefully be the thread to whack the final nail in this bug's coffin, namely:

WHERE ARE MY WINDOW DECORATIONS?

*cough*

I'm using beryl now, because compiz was no-go; there are serious compatibility issues between the various packages when installing through apt-get. Anyway, I've managed to bypass the lack of window decorations by switching to Heliodor rather than Emerald as my window decorator, but I'm not really familiar with it. 

Some questions: how do I change the theme? Can it even be done? And, most importantly, why does emerald not work?

I know the problem is not with ME, because:
Hardware - beryl worked perfectly 3~ months ago
Software - I've just done a fresh install of Feisty.


Thoughts?
Helidor uses the same theme as Metacity (the gnome default WM), so just find a metacity theme and install/enable it in System -> Preferences -> Theme

---

### Post by hoboken on 2007-09-20
Nice. What are my chances with  compiz, though? In terms of user experience, it is miles ahead of but like I said, it has these compatibility and update problems which kill the window decorations. Is it just a case of waiting until they sort the packages out?

---

### Post by joehill on 2007-09-21
Hi,

What compiz repository have you been using?  I was using Treviño's repository for a while but it kept breaking and whatnot because it's updated from unstable sources.  (I had the same problem of no decorations.)  I subsequently found out there's a more stable repository maintained by Amaranth from sources backported from Gutsy.  This page ([https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)) gives instructions, which are basically to add this to /etc/apt/sources.list:

deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main
deb-src [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main

then

sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install compiz compizconfig-settings-manager 

But simply upgrading didn't do it for me though.  Before using the new repisotory, I had to remove previous third-party repositories and then do this:

sudo apt-get --purge remove compiz* libcompizconfig*

The other thing is, if you're using Nvidia, you may still lose your decorations until you do this:

sudo nvidia-xconfig --add-argb-glx-visuals -d 24

---

