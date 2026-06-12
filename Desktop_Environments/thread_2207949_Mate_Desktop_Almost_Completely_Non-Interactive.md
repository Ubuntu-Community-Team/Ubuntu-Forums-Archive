---
title: "Mate Desktop Almost Completely Non-Interactive"
date: 2014-02-25
forum: Desktop Environments
---

### Post by ufarmer on 2014-02-25
I just finished a clean install of 12.04 and installed Mate as follows:

sudo add-apt-repository "deb [http://packages.mate-desktop.org/repo/ubuntu](http://packages.mate-desktop.org/repo/ubuntu) precise main"
sudo apt-get update
sudo apt-get --yes --quiet --allow-unauthenticated install mate-archive-keyring
sudo apt-get update
# this installs base packages
sudo apt-get install mate-core
# this installs more packages
sudo apt-get install mate-desktop-environment

According to the instructions found here:

[http://wiki.mate-desktop.org/download](http://wiki.mate-desktop.org/download)

Everything seems to have proceeded smoothly and I am able to log into Mate.  However, even though the cursor can be moved and hovering over the network icon displays information about my network connection, I cannot click on anything or even launch a terminal using keyboard commands.  I have googled and googled with no luck.  One poster in a forum thread said they had solved the same problem by updating their kernel, however, as I just did a clean install today, my kernel is much newer than the one mentioned in the post.

Any advice is appreciated.

---

### Post by monkeybrain20122 on 2014-02-25
It wouldn't be a kernel problem since you could launch terminal and use keyboard commands before you installed Mate (you installed it with terminal and commands)

---

### Post by ufarmer on 2014-02-25
Yeah.  I should have mentioned that in Unity everything is fine.  It might be worth noting that originally I did an upgrade from 10.04 on a Lenovo ThinkPad T500, installed gnome-fallback, and absolutely everything in Gnome was buggy: freezing, crashing, overheating (!!!).

---

### Post by tgalati4 on 2014-02-25
I would have installed a clean version of Linux Mint MATE, since it works out of the box.

Do you have these installed?

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

---

### Post by ufarmer on 2014-02-26
I think a clean installation of Mint is the way this is headed.  I should have read more about 12.04 before I upgraded/reinstalled.  Ubuntu has been working for me so well for so long that I just never anticipated they would make such a mess of things.  The fact that one cannot move the launcher or the menu bar in Unity just blows my mind.

---

### Post by buzzingrobot on 2014-02-26
You installed Mate correctly, so it would be interesting to see what went wrong. I've installed Mate on every release from 12.04 forward without problems.

Mint 16 Mate is very nice. If you get nosey, you'll see a few non-visual pieces of Unity in there because some apps in the Ubuntu repos -- where Mint pulls from -- are linked with Unity libs.

---

### Post by ufarmer on 2014-02-26
Thanks.  I have checked and checked and, by all accounts, the installation was correct and did not complain.  Also, much googling does not turn up any problems similar to mine.  It was essentially impossible to isolate the problem since everything was a mess.  I was almost always frozen right after logging in and the overheating was really alarming.  I just won't risk frying the cpu over this.

---

### Post by tgalati4 on 2014-02-26
Sounds like your install went bad.  It's rare but it happens.  Installing a new desktop environment is almost as painful as a full install.  Unity follows precisely defined guidelines.  It may be too restrictive for you.

---

### Post by oldrocker99 on 2014-03-06
I love MATE, and dislike Mint. I'm running (right now) Lubuntu 13.10 with MATE 1.8 (which updated last night).

---

