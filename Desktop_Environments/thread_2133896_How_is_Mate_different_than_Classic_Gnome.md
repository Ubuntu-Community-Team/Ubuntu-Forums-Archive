---
title: "How is Mate different than Classic Gnome?"
date: 2013-04-09
forum: Desktop Environments
---

### Post by GregA on 2013-04-09
How is Mate different than Classic Gnome . . . are they compatible and interchangeable anymore . . . . or has Mate incorporated new features, files, libraries, etc.?   Why would one choose over the other?

Greg

---

### Post by Frogs Hair on 2013-04-09
Mate is a fork based on pure Gnome 2 and retains features from Gnome 2 such as the file manager , appearance preferences , panel and indicator function(re-branded) and is not interchangeable with classic. There are number of tweaks available in classic that can make them similar . [https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)   

The appearance preferences in Mate cannot be duplicated in classic.  [http://en.wikipedia.org/wiki/MATE_%28desktop_environment%29](http://en.wikipedia.org/wiki/MATE_%28desktop_environment%29)

---

### Post by tgalati4 on 2013-04-09
Mate works and it is fast on 4 machines that I have tested it on.  All of the gnome packages have been renamed to avoid conflict with gnome/gtk frameworks.  For instance instead of gnome-calc it's mate-calc.  Instead of nautilus it's caja.  Instead of gedit it's pluma.  So other than the name changes, it runs well.

Some mate packages:

mate-backgrounds - a set of backgrounds packaged with the MATE desktop
mate-bluetooth - MATE Bluetooth tools
mate-calc - MATE desktop calculator
mate-conf - MATE configuration database system
mate-conf-common - MATE configuration database system (common files)
mate-conf-editor - An editor for the MateConf configuration system
mate-control-center - utilities to configure the MATE desktop
mate-core - MATE Desktop Environment (essential components)
mate-desktop - Library with common API for various MATE modules
mate-desktop-common - Library with common API for various MATE modules (common files)
mate-desktop-dbg - Library with common API for various MATE modules (debugging symbols)
mate-desktop-environment - MATE Desktop Environment
mate-desktop-gnome - Library with common API for various MATE modules (GNOME files)
mate-dialogs - Display graphical dialog boxes from shell scripts
mate-dialogs-gnome - Display graphical dialog boxes from shell scripts (GNOME files)
mate-icon-theme - MATE Desktop icon theme
mate-icon-theme-faenza - MATE Faenza Desktop icon theme
mate-media - MATE media utilities (metapackage)
mate-media-common - MATE media utilities
mate-media-gstreamer - MATE media utilities (GStreamer backend)
mate-media-pulse - MATE media utilities (PulseAudio backend)
mate-menus - implementation of the freedesktop menu specification for MATE
mate-notification-daemon - daemon to displays passive pop-up notifications
mate-panel - launcher and docking facility for MATE
mate-panel-common - launcher and docking facility for MATE (common files)
mate-power-manager - power management tool for the MATE desktop
mate-power-manager-common - power management tool for the MATE desktop (common files)
mate-power-manager-dbg - power management tool for the MATE desktop (debugging symbols)
mate-screensaver - MATE screen saver and locker
mate-session-manager - MATE Session Manager
mate-settings-daemon - daemon handling the MATE session settings (metapackage)
mate-settings-daemon-common - daemon handling the MATE session settings (common files)
mate-settings-daemon-gstreamer - daemon handling the MATE session settings (GStreamer version)
mate-settings-daemon-pulse - daemon handling the MATE session settings (PulseAudio version)
mate-text-editor - official text editor of the MATE desktop environment
mate-themes - official themes for the MATE desktop
mate-utils - MATE desktop utilities
mate-window-manager - MATE lightweight GTK+ window manager (metapackage)

Because of the name changes, it should be able to reside alongside gnome3 environments, although I have not tried it.

The new Pope drinks mate, so it must be good.

---

### Post by zombifier25 on 2013-04-10
GNOME Classic is also being retired in favor of a custom "classic" GNOME Shell config, so if you want authentic GNOME 2 (in the foreseeable future), stick to MATE.

---

### Post by GregA on 2013-04-10
Thanks for the info.   I'm running Kubuntu 12.03.2x now, . . . . if I wanted to try Mate, is it available in the standard repository, or do I need to add a PPA?   

I'm still fine with KDE and Kubuntu, but I did run classic gnome for about 5 years, and would like to add it to the startup desktop options (along with Cinnamon, XFCE, even Unity, etc.).   Is that easily do-able in Kubuntu LTS - - I know many users intall Mint to use these DE's . . . but I'd like to see if I can achieve the same result by just updating Kubuntu?  

Would adding all these althernate Desktop Environments tend to make Kubuntu unstable???  If that's the case, I would only do this on an older "sandbox" laptop where I can "play" . .

---

### Post by Frogs Hair on 2013-04-10
Mate is only available from a PPA right now. Install and use at your own risk as with all PPAs.  [http://www.webupd8.org/2013/04/mate-16-released-install-it-in-ubuntu.html](http://www.webupd8.org/2013/04/mate-16-released-install-it-in-ubuntu.html)

---

### Post by tgalati4 on 2013-04-10
Or install Linux Mint Mate and then install additional desktop environments.  Mate is supported in the main package Linux Mint repository.  I have  no experience with multiple DE's with Mate, so you will have to try it and see how it works.  You might want to spend some time on the Mint forums to see how others are doing with multiple DE's.

---

### Post by Vontux on 2013-04-12
> **tgalati4 said:**
> Or install Linux Mint Mate and then install additional desktop environments.  Mate is supported in the main package Linux Mint package repository.  I have  no experience with multiple DE's with Mate, so you will have to try it and see how it works.  You might want to spend some time on the Mint forums to see how others are doing with multiple DE's.

I am running Linux Mint 14 Cinnamon edition right now. I happen to be running Mate as I ended up finding it more stable than Cinnamon. I have Mate, KDE, and Cinnamon all happily co-existing on this machine, so I don't think you'll run into any problems running multiple desktop environments. One thing I have noticed is that many of the renamed packages have also had updates to their UI and underlying code, "pluma" the mate version of "gedit" has a somewhat different UI, and so does mate's calculator compared to gnome's.

---

### Post by FiremanEd on 2013-05-25
I have a feeling that MATE has a bit way to go to become a semi-major player (it's appears to be still running "on the baseball's equivalent of a farm team".  Cinnamon has it's issues as well. For example, battery indicator seems stuck while you work on battery. It always shows I'm at 100% and won't respond being on battery only. All in all, but it's moving along nicely.  Time will tell.

I use MATE on Ubuntu 12.04 with Unity stripped down and away to boot into MATE only on my 1.6 ghz, 2g RAM by ACER Aspire.  Runs like a dream.  No hesitations. no lag or darkneing of screens while it thinks.  Two years of support on 12.04 LTS.  Winner.

---

### Post by ben2talk on 2014-02-28
I cling to Mate. With synapse added, a nice dock at the bottom, small cocky for networking/ hdd status etc. Perfect! Tried others, too easily broken - dont bend easy enough. Tried adding kwin - messed up shortcuts n settings too much. 

Plain Mate - looks gorgeous with Variety installed to do wallpaper/clock/quote. 

Needs slightly improved window animations....

---

### Post by ben2talk on 2014-02-28
I wouldn't .... Try a fresh install first. Not sure KDE is friendly enough... Just installing n removing Kwin gave me hours of fun.
I'd recommend the Mint DVD to install it too, my experience brings me back to it as it gives the most comprehensive install. Biggest issue (compared with booting Win7) is getting only stereo digital (Win7 gives me 5.1 with the option to turn off my non-existing centre/subwoofer out of the box).

---

### Post by ben2talk on 2014-02-28
Installing Mate is good, but many issues still arise if you try out another DE - changing settings and stuff. My advice is to put your stuff out of /home (music n pictures n stuff) and try it as a dualboot. 
Installing kwin was nice, but my keyboard shortcuts were screwed - I'll be more careful next time.

---

