---
title: "[SOLVED] Help installing desktop environments!"
date: 2008-04-07
forum: Desktop Environments
---

### Post by mjp216 on 2008-04-07
Ok, I run 7.10 Gutsy and i would like to know how (if possible) to install KDE and/or XFCE but not have them dominant over my existing desktop environment (Gnome). I just want to have the option to log on in either KDE, XFCE, or Gnome as a session, when i log on. Thanx in advance.

---

### Post by SunnyRabbiera on 2008-04-07
Oh yes you can install the other desktop environments without it messing up your computer.
what one do you want to use?
KDE?
XFCE?

---

### Post by mjp216 on 2008-04-07
Kde

---

### Post by Tuxoid on 2008-04-07
alright, 

-Open up your package manager under System>Administration>Synaptic Package Manager

-click the search button on the toolbar

-this is where you need to make your desicion on what additional Desktop Environments you want:

if you'd like KDE, search 'kubuntu-desktop' (no quotes)
for xfce, search 'xubuntu-desktop'

-once you've search for one of these, it should show a package of the same name
click the box next to the package and select 'Mark for Installation'

-it will download the desktop of your choosing

After you have downloaded one (or both) of these desktops, to use them you will need to log out and at the log in screen, go to 'Options'>Select Session

From here, you will see all the currently installed desktop environments (and some usually erroneous options)

Select which desktop you'd like to log into and go with it.:popcorn:

---

### Post by mjp216 on 2008-04-07
Thank you!

---

### Post by antemon on 2008-04-07
here's a Q though, sorry total newb.

If there's a new release of a desktop environment, i read somewhere the GNOME or something (which I think is what 8.04 has) had a new one up, can I install that and not screw up my computer?

---

### Post by Tuxoid on 2008-04-07
Yes, you can two versions of the same desktop environment, but I wouldn't suggest it.

At one point I had KDE 3.5 and KDE 4.0 on my machine, but by installing KDE 4.0, my KDE 3.5 Help System got screwed up.

This most likely would have different repercussions with Gnome or XFCE, and they could be serious.

You'd also have to track-down a .deb package for Gnome 2.22 on the internet since it's not listed in the Ubuntu software database yet.

and the Gnome package you get from say, gnome.org may not be configured in a way to work with everything. This usually won't affect anything major, just small stuff like media keys on laptops.

I'd suggest waiting until the next of Ubuntu. It should have Gnome 2.22 by default.

---

