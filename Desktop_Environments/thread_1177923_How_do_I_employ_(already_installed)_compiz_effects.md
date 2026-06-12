---
title: "How do I employ (already installed) compiz effects in KDE ?"
date: 2009-06-03
forum: Desktop Environments
---

### Post by bobdobbs on 2009-06-03
Hi all.
I'm using ubuntu 9.04. I've been using gnome for ages.
But I decided that I want to check out KDE. 

I have compiz working perfectly under gnome. 
When I switch to KDE, and I use CTRL+ALT and the arrow keys, I expect to get the desktop cube effect.

But I don't get it.

So, as far as I can tell, I can't access the compiz effects under KDE.

Is there a way to employ the cube (and other compiz effects) under KDE ?

Thanks.

---

### Post by Chronon on 2009-06-05
I use CCSM (CompizConfig Settings Manager) to choose which effects I want and configure them.

---

### Post by krazyd on 2009-06-05
KDE uses the kwin window manager which has it's own desktop effects. It is a different program to compiz and works better with KDE.

To configure desktop effects go to System Settings > Desktop > Desktop Effects, and select the 'all effects' tab.

To get the effect you want, enable and then click the configuration button of the 'Desktop Cube' plugin. in the 'advanced' tab select to 'use this effect for walking through desktops' and/or 'display the cube when switching desktops' (play with these settings to get the effect you want).

Then go to System Settings > Keyboard & Mouse > Global Keyboard Shortcuts. Select 'kwin' from the 'KDE component' dropdown. Select the actions and whatever key combo you want. There are actions such as 'Switch one desktop down', 'Switch one desktop to the left', 'walk through desktop list' etc. depending on the effect you want.

enjoy your cool, compiz-free composited desktop!

---

