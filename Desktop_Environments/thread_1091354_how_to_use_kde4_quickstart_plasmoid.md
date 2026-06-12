---
title: "how to use kde4 quickstart plasmoid"
date: 2009-03-09
forum: Desktop Environments
---

### Post by equaeghe on 2009-03-09
Hi,

I would like to use the kde4 quickstart plasmoid.
However, adding applications seems nontrivial: when selecting 'add' it brings up a dialog which needs a *.desktop file. Where in my filesystem can I find such files for firefox, krusader, konsole, alpine,...? Should I make them myself?

Erik

---

### Post by d80tb7 on 2009-03-09
Hi Erik,

you can just drag icons from the menu onto the quicklaunch.  It seems to be a bit picky about how precise you need to be to do this though and it always takes me a couple of goes.

hope that helps,

Chris

---

### Post by tarahmarie on 2009-03-10
I'd like to know if anyone's had any problems with the icons in the Quicklaunch plasmoid becoming TINY when adding more than one or two.

---

### Post by equaeghe on 2009-03-10
> **d80tb7 said:**
> 
you can just drag icons from the menu onto the quicklaunch.  It seems to be a bit picky about how precise you need to be to do this though and it always takes me a couple of goes.

hope that helps,


Thanks Chris, it does. (Without pickyness, even.)

---

### Post by equaeghe on 2009-03-10
> **tarahmarie said:**
> I'd like to know if anyone's had any problems with the icons in the Quicklaunch plasmoid becoming TINY when adding more than one or two.

Yes. Wat I did to circumvent this was put multiple quicklaunch plasmoids on the toolbar and put only one icon per plasmoid.

Erik

---

### Post by d80tb7 on 2009-03-12
yes that's a know bug, see [https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/334137](https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/334137)

it looks like it should be fixed soon though.

Chris

---

### Post by tarahmarie on 2009-03-13
Anyone know when the next kdebase release is?  I'm dying without my quickstart plasmoid!

---

### Post by cptr13 on 2009-03-15
Maybe I'm misunderstanding the point of this post but I use this plasmoid just fine.

Drag and drop icons from the kmenu.

You can change the settings to allow more rows/icons.

Then just adjust the (overall plasmoid) size like any other plasmoid.  That will increase/decrease the size of the icons.


I've never had issues with this.  Does this help?

---

### Post by tarahmarie on 2009-03-16
> **cptr13 said:**
> Maybe I'm misunderstanding the point of this post but I use this plasmoid just fine.

Drag and drop icons from the kmenu.

You can change the settings to allow more rows/icons.

Then just adjust the (overall plasmoid) size like any other plasmoid.  That will increase/decrease the size of the icons.


I've never had issues with this.  Does this help?

In the panel, the size of the plasmoid is predetermined and unsizable.  That's the problem; until kdebase is fixed, dragging and dropping icons to the quicklaunch in a panel just makes the icons TEENY.

---

### Post by tarahmarie on 2009-03-16
Here's a quick hack to get around it; create multiple quicklaunch plasmoids in your panel, and only put two icons in each.  That gives me my standard 2x6 quicklaunch look.

---

### Post by bryancd2 on 2010-11-25
I seem to have a new twist on this problem.  One problem leading me into another.

Original problem (which still remains) is that I dual-boot WinXP and Kubuntu.  My thunderbird mail and firefox files, profiles & messages are all on a dedicated fat32 drive.  So, from WinXP or kubuntu, I was able to always get to my messages or firefox profile settings, etc.  

First problem:
Then for some reason neither firefox or thunderbird wants to launch from kubuntu anymore.  Got the dreaded application already running message, and have verified that no parentlock files exist anywhere.  No problems using thundebird or firefox from WinXP.

Second problem:
Out of frustration, I attempted to re-install firefox (kubuntu).  Used apt-get remove, then apt-get install, etc.
a)  firefox still did not run because it claimed the same old parentlock like problem (Firefox is already running, but not responding)
b)  can't get the plasmoid icon back into the quicklaunch bar of kde4 to save my life!?

Truly frustrated!

Bryan.

---

