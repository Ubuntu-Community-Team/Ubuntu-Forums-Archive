---
title: "Crystal SVG Icons no working in 7.10"
date: 2007-10-27
forum: Desktop Effects &amp; Customization
---

### Post by Kevin Carmony on 2007-10-27
I go to System > Preferences > Appearance

I then click the Customize button and then the Icons tab.  As I select each of the different icon options, I see the icons on my desktop change, EXCEPT when I click on the Crystal SVG icons.  I have two questions...

1. Why does it show TWO Crystal SVG options (all others just have one)?

2. Why when I select either of the Crystal icon themes, it just uses the regular default GNOME icons?  (All the others work.)

Thanks,

Kevin

---

### Post by smartboyathome on 2007-10-27
1. It could be that there are two folders with two icon setups for Crystal icons.
2. The Crystal icons may not exist, and they default to GNOME.

---

### Post by Kevin Carmony on 2007-10-28
In the usr/share/icons folder there is only one folder for the Crystal fonts (crystalsvg), but there is a default.kde shortcut folder which points to the Crystal fonts, so I'm pretty sure that explains why this option appears two times.

However, when I look in the crystalsvg folder, all looks fine and the fonts are there, but they aren't being used when I select the Crystal SVG option from the Configure dialog box.

Kevin

---

### Post by nuir on 2007-10-31
I have the exact same problem, in fact, it's been like that for me since feisty fawn. I never found a solution, so I just downloaded a Crystal theme from gnome-art and that was it...

It doesn't bother me too much though... but I wonder if anyone knows a way to change the default icons for a file type. I tried changing it manually from the properties windows of a file, but ended just changing the icon of that individual file. This is one of the few things I actually miss from Windows. 8-[

---

### Post by FuturePilot on 2007-10-31
Yeah, that theme has never worked as far as I can remember. I have no clue why.:confused:

---

### Post by Kevin Carmony on 2007-11-01
Where do I log a bug for this?  (Newbie alert! =)  I'm guessing it's an easy fix.  I believe in fixing all these little things, as it's the little things that make you "feel" you can trust your OS.  If Linux is to be "better" than Microsoft, we should pay attention to all the little details as well.  First step, get the bug logged.  Where do I do that?

Kevin

---

### Post by VictorR on 2007-11-01
Neither it worked for me. 
But after reading these posts I did investigate the issue and found this:
1. the index.theme file contains some stuff, which indicates that this icon set was designed not for Gnome, but rather for KDE.
2. some folders named differently (comparing with other icon sets), for example "places" <-> "filesystems"
3. its inherits Gnome (icon set), that means, if something goes wrong (a particular icon does not exist or definition is missed) it takes the icon from the Gnome set.
4. Maybe Type=Threshold is a wrong definition for Gnome, what causes rejection of the whole set.

Can someone confirm or disprove my results?

---

