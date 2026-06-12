---
title: "How do I make multiple sessions, one with compiz-fusion and another for gaming"
date: 2009-03-23
forum: General Help
---

### Post by nullhility on 2009-03-23
I've scoured the Internet and most of the results looked a little "dirty" compared to an official "howto" that's guaranteed not to break my system. So I figured that maybe I'd give asking a go.

The problem:
    After installing some games through wine and finding that they run ridiculously slow, whether or not I'm using direct draw or openGL (which seemed to be worse) rendering, I decided to attempt making a "game user" which had no desktop effects enabled (seeing as the main user had compiz-fusion enabled and a whole lot of 3d acceleration hogging eye-candy). But this turned up the same results. I've tried playing around with nVidia settings (restricted driver) to no avail and even attempting to override libraries in wine.

The Question:
    So is there a way I can create a session for the main user (I saw something about swapping between custom xsessions somewhere) and a session for gaming, where one has all the effects and the latter frees up all the hardware acceleration so the games can use them (I'm not terribly literate with graphics or X settings so forgive me if anything I've asked doesn't seem to make sense).

System specs:
RAM: 1 GB
Graphics: nVidia GeForce FX 5200
CPU: AMD Sempron Processor 2800+ 1599.537 MHz
Desktop: Gnome 2 Ubuntu Intrepid Ibex (8.10)
Wine version: wine-1.1.17

$ compiz --version
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
compiz 0.7.8

Thanks for your time :)

---

### Post by aeiah on 2009-03-23
from what you're saying you havent actually managed to get it running ok? what games are you trying to run? i imagine something like doom 3 / quake 4 etc might be pushing your cpu and graphics card a bit

---

### Post by Locutus_of_Borg on 2009-03-23
the very easiest way would be to install a second desktop environment (xfce or something) and select it instead of gnome when you want to run games, rather than having two separate gnome sessions

---

### Post by nullhility on 2009-03-23
The games I was trying to run are Red alert 2 and Unreal tournament 2004, and from what I understand I have the above minimum recommendation for both, but they've both been too slow to be playable. I didn't think of installing a seperate desktop environment but I am trying to conserve disk space (3GB left on the main HDD) so the smaller the better and what should I do to install a working version?

I went ahead and installed xfce4, rebooted and logged into a xfce session, it was nice, although compiz was enabled by default and I couldn't turn it off, the same problems with the games persisted.

---

### Post by nullhility on 2009-03-24
bump!

---

### Post by Locutus_of_Borg on 2009-03-24
why can't you turn off compiz in xfce?

---

### Post by nullhility on 2009-03-24
Well when I go into xfce settings I can't seem access the window manager or the window manager tweaks sections. I get an error message saying that it can't work with the the current window manager. I did however use the fusion icon to switch the window manager, loaded a game up and no cigar still. I was wondering as well if turning the Composite extension off in my xorg.conf file would help (wine wiki mentions doing this by the way), but would I still be able to use compiz-fusion after doing that?

---

### Post by Barriehie on 2010-01-31
> **nullhility said:**
> Well when I go into xfce settings I can't seem access the window manager or the window manager tweaks sections. I get an error message saying that it can't work with the the current window manager. I did however use the fusion icon to switch the window manager, loaded a game up and no cigar still. I was wondering as well if turning the Composite extension off in my xorg.conf file would help (wine wiki mentions doing this by the way), but would I still be able to use compiz-fusion after doing that?

What about using metacity --replace in a terminal?

Barrie

---

