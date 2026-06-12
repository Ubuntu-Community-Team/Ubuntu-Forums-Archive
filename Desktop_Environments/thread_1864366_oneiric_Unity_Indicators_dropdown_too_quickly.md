---
title: "oneiric: Unity Indicators dropdown too quickly"
date: 2011-10-18
forum: Desktop Environments
---

### Post by Cahoots N Boots on 2011-10-18
This is a minor concern but annoying.  After fresh installing 11.10 (64-bit) whenever I click an indicator in Unity at the top panel (attached thumbnail), ex. power button menu or network connections, the dropdown menu does not stay -- unless I hold down the mouse button.  The menus/dropdowns will not hold and they go away too quickly (unless, like I said, I hold down the mouse button while selecting).  Is there any way to fix this?

On my laptop (x86 11.10) the Unity indicator drop-downs work just fine, when I click the network dropdown, well... it stays down!  Unless I click off or change windows, I don't have to hold a mouse button.

I didn't see any settings in dconf-tool I could use.  Also I checked out the compizconfig settings manager (ccsm) but I didn't see any settings for this.  Maybe I missed it?  Is there a unity setting I didn't find?

My only thought is that perhaps my nvidia drivers are causing some issues.  Newest driver: 285.05.09.

Any help is much appreciated!  Thanks!

---

### Post by wildflower1975 on 2011-10-18
I'm getting weird behavior from the Menu Bar too after an upgrade to 11.10.

When I try to hover over the volume icon (I want to access the Banshee menu), the menu bar disappears gets redrawn. As the Menu bar is redrawn, the Icons on my desktop and sometimes Window chrome is jiggled.

I too have NVIDIA drivers.

---

### Post by Myoldmopar on 2011-10-19
I can confirm the menu behavior in OP.  If I click on any panel (clock, user, settings, indicator-weather), the drop down menu is only visible while I hold the mouse button down.  If I release it goes away.  This behavior is not consistent, as if I reboot, it doesn't do it.  I have not narrowed down what initiates this problem.

I am using nvidia 285 from x-swat on a Dell L702X GT555M 3D; Oneiric 64-bit upgraded from Natty 64-bit.

---

### Post by Cahoots N Boots on 2011-10-22
Testing it on my dual monitors the problem only seems to affect one monitor and not the other.  Usually it's the secondary monitor, but not always.

I removed the nvidia drivers and reset all system graphics drivers to default and I'll see if that resolves the issue later, and I guess just wait until nvidia drivers are a bit more stable with 11.10.

---

### Post by amenon81 on 2011-10-24
I have the exact same problem with my dual monitor setup - the issue shows up on one of the monitors but not the other. I don't think that it is a graphics card issue - mine is an integrated Intel card that uses the open source driver. This happened after the upgrade to 11.10

---

