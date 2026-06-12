---
title: "Visual effects on appearance settings not working."
date: 2008-02-12
forum: Desktop Effects &amp; Customization
---

### Post by Kivech on 2008-02-12
Hi all,

I'm running Ubuntu 7.10 and after install and update I started configuring my system.

Trying to up the display settings of the Appearance Preferences I wanted to maximize my desktop experience. I can use all tabs, however when I select the last tab (Visual Effects) I get the options to increase effects (default none is selected) but the second I select one of the other options it locks up and I get an error message (the composite extension is not available), which is like chinese to me. The only way to quit it is to kill the process.

I'm running Ubuntu out of the box with ATI Radeon drivers. Ran the updater and it updated it all.

So what am I missing here. I tried to run some 3D games for a test but it seems I have to install some packages to use those options. Could these be related?

Any suggestions would be highly appreciated. For sure my system can handle any gfx load, so that can't be the problem.

Kivech

---

### Post by snow_56767 on 2008-02-18
Hi,
    Those packages for the games your trying to run are (if anything) necessary.
This is because The visual effects are almost 100% 3D. You should also find your
graphics card kernel source in synaptic Package Manger.
Also look for a driver in Restricted Driver Manger (system > Administration > Restricted Drivers        Manager).
 Also what Kind of Graphics card do you have, and does it support 3D?

---

### Post by dantheman68 on 2008-02-20
AHHH... I too have an ATI Radeon card. I just installed Ubuntu today, and was having fun messing around on the higher settings, then i went to change the bootloader so that it would load XP pro by default, the next time i booted linux, i could only choose the "none" setting, and would get error messages!!

---

### Post by dantheman68 on 2008-02-20
ok, i think i just got it figured out, im running a Radeon 9200, This worked for me....

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
scroll down to where it says:
Removing the proprietary fglrx driver
follow the instructions... and like i said... it worked for me :)

---

