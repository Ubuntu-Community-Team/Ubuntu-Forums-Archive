---
title: "OK, how do I get rid of the compiz whatever"
date: 2008-01-09
forum: Desktop Effects &amp; Customization
---

### Post by paul cooke on 2008-01-09
and just have a normal desktop?

I've just installed a cover disk version of Gutsy, not bothered with setting up accelerated graphics (I don't need it) and I want to get rid of this thing that's causing xorg to sit there using at least 20% processor and making my desktop decidedly unsnappy...

I want to get rid of it for KDE, Gnome and Xubuntu desktops...

---

### Post by rune0077 on 2008-01-09
System > Preferences > Appearances ... click visual effects and set it to none. 

Your problem is very likely not Compiz, though, since it doesn't use any processor power while the effects aren't used - by which I mean, if you spin the cube for instance, processing power will be used, but as soon as the cube is spun and the animations are over, Compiz no longer uses CPU-power. So if 20% CPU is being used while you're not actually doing anything at all, then I don't think Compiz is your problem.

---

### Post by paul cooke on 2008-01-09
well this is weird... I just accidentally disconnected the power lead and the laptop went onto battery power... the cpu usage promptly dropped to 0% and when I put the lead back in it went back to 20%...

while the machine is on batteries, the desktop is snappy and menus etc. appear far faster...

could my CPU throttling be back to front?

Sony VAIO PCG-FR415B

I've just enabled ACPI support in the KDE laptop battery panel application and I've told it not to throttle when on mains...

I'm rebooting it now.

got to anyway, I've just been installing ubuntu-studio

hah... massive difference... booted up in a fraction of the time and everything now feels as it should...xorg is now just idling at 1.5%

now to work out why I've got no boot-splash and then maybe see if it's worth enabling 3D acceleration with this box...

---

### Post by rune0077 on 2008-01-09
Splash screen is weird in Gutsy. You can set it manually through Compiz somehow (can't remember exactly where).

---

