---
title: "Desktop Effects and Multiple Monitors"
date: 2008-12-14
forum: General Help
---

### Post by rcoconnell on 2008-12-14
Previously, I had Intrepid running ok on an Acer Aspire One.  This included desktop effects, with Avant window navigator and (for good measure) gnome-do.  I made the gigantic mistake of hooking up a second monitor (spanning), and after a bit of wrestling actually got that to work as well.  At the expense, apparently, of desktop effects, AWN, and gnome-do.

I'm not sure how to trouble-shoot this problem.  In previous versions of ubuntu I would have started with xorg.conf, which the "Screen Resolution" applet might have modified, but I don't know what files "Screen Resolution" modifies these days.  All I can report is that if I go into "Appearance", then the "Visual Effects" tab, and try to set them to "Normal," all I get is "Desktop effects could not be enabled."

-ross

---

### Post by Ng Oon-Ee on 2008-12-15
What card are you running? The fact that your tag says Twinview leads me to believe it is an Nvidia. How did you try to setup the second monitor? There's a whole lot of guides in these forums to setting up a dual-screen, or a dual-screen with NVidia. May I suggest following one of them?

---

### Post by rcoconnell on 2008-12-16
The graphics hardware is GMA950.  Twinview was just a guess.

In order to set up the second monitor, I (a) plugged the monitor into the VGA port and (b) opened "screen resolution" applet.  In that, I set the resolution for the external monitor, adjusted the relative positions, and was told that I needed to log out and log in again.  I believe that it modified... some file.  I can't reproduce the original behavior (since "screen resolution" seems to consider everything to be set up now), so I haven't been able to figure out what file might have been modified.

My question is, I think, much more basic.  Incredibly elementary, actually.  What has replaced xorg.conf as the place where monitors, etc., are configured?

-ross

---

### Post by iponeverything on 2008-12-16
You can find your original xorg.conf in /etc/X11 -- it will have an extension like 20081210100831 that will be the timestamp from when the resolution applet replaced it. If you copy it back into place of the xorg.conf you will be good to go.  Another way to revert would be to boot into recovery mode and run xfix.

BTW -- don't forget to logout and log back in for the new xorg.conf to be used.

---

### Post by rcoconnell on 2008-12-16
THanks for the tip.  I wound up running 

sudo dpkg-reconfigure -phigh xserver-xorg

which for me would have been equivalent to restoring one of the old xorg files.  The two versions are pretty similar, except that the one where compiz is broken has

SubSection "Display"
     Virtual 2000 768
EndSubSection

I presume this virtual display is what spans the two monitors?  And that this is a bigger display than the GMA950 can run desktop effects over?

Ah well.

---

