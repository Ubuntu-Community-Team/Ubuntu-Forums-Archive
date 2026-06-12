---
title: "can't get laptop brightness annoyances"
date: 2009-02-19
forum: General Help
---

### Post by myknbani on 2009-02-19
Hi folks, my first post,

I have ubuntu on my laptop (MSI GX600), and when I press the keyboard shortcut for changing LCD brightness, it used to show an OSD, with the sun (i think), and a bar.  But just recently (don't remember exactly when), i noticed that it's no longer showing up when I press the keys, but i can dim and brighten my laptop with no problem.  The OSD now only shows when I plug and unplug the AC power.

Using the brightness applet, it has an initial incorrect reading of 50% no matter how bright or dark my display is.  When i adjust the slider, it gives the message on the icon's tooltip:  Cannot get laptop panel brightness (icon changes to sun with red error icon).

My OSD for volume is fine though.

I really don't know how this happened, but i did lots of things prior to me, noticing this weirdness.  I don't know the exact cause, but my last three package installations are my prime suspects.

1.  installed kubuntu-desktop
2.  installed Compiz CCSM
3.  installed updates, which contains the following (from synaptic history):

[INDENT]Commit Log for Mon Feb 16 22:18:05 2009

Upgraded the following packages:
consolekit (0.2.10-1ubuntu9) to 0.2.10-1ubuntu10
dpkg (1.14.20ubuntu6) to 1.14.20ubuntu6.1
gvfs (1.0.2-0ubuntu1) to 1.0.2-0ubuntu2
gvfs-backends (1.0.2-0ubuntu1) to 1.0.2-0ubuntu2
gvfs-bin (1.0.2-0ubuntu1) to 1.0.2-0ubuntu2
gvfs-fuse (1.0.2-0ubuntu1) to 1.0.2-0ubuntu2
hal-info (20081124-0ubuntu1~intrepid) to 20090128-0ubuntu1~intrepid2
libck-connector0 (0.2.10-1ubuntu9) to 0.2.10-1ubuntu10
libgvfscommon0 (1.0.2-0ubuntu1) to 1.0.2-0ubuntu2
libpam-ck-connector (0.2.10-1ubuntu9) to 0.2.10-1ubuntu10
rhythmbox (0.11.6svn20081008-0ubuntu4.2) to 0.11.6svn20081008-0ubuntu4.3[/INDENT]

I did a lot of things to try and fix this thing (blindly).  It's not that big of a problem but I know something is messed up. :(

1.  Google and ubuntuforums search.
2.  Reset my Compiz settings, both from CCSM and Appearance Preferences.
3.  I tried to uninstall kubuntu-dekstop and guidance.
4.  Tried to reinstall ubuntu-desktop and gnome-power-manager.
5.  Reinstalled some packages bravely and stupidly (oh my!)
[INDENT]acpid (1.0.6-9ubuntu4)
apmd (3.2.2-10ubuntu1)
powermanagement-interface (0.3.18)
powermgmt-base (1.30)
hal[/INDENT]
6.  Moved to trash my gnome settings (.gnome2, .gconf, .gconfd).
7.  Created a new user for comparison (no OSD there too).
8.  Booted ubuntu and kubuntu live CDs for comparison:
[INDENT]There is a brightness and sound OSD for ubuntu, but only sound OSD for kubuntu.[/INDENT]

So in summary, brightness works but no visual feedback on the percentage of brightness.

Thanks in advance!  I'll try to be more observant and be more careful next time so that I can backtrack easily.  This is not really of high priorty aside from me wanting my OS to feel normal! :biggrin:

---

