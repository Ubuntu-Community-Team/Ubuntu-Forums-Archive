---
title: "It's gone... all gone..."
date: 2013-10-13
forum: Desktop Environments
---

### Post by RogerDavis on 2013-10-13
Everything on the bar on the bottom of the screen - Desktops, open apps, the icon to clear the screen, etc. -  all of them - the bar is completely empty !

Three separate error messages on each boot say:

The panel encountered a problem while loading   WnckletFactory::WindowListApplet
The panel encountered a problem while loading   WnckletFactory::ShowDesktopApplet
The panel encountered a problem while loading   WnckletFactory::WorkSpaceSwitcherAplet

These all happen on every boot.

I'm using gnome desktop.

How can I fix this / these ?

---

### Post by TheFu on 2013-10-13
Sorry, I don't have a fix, but have a few ideas.
1) have you tried turning it on and off?   sorry, my IT crowd love forced that to come out. ;)
2) have you tried reinstalling gnome?
3) have you checked for bad/failing hardware?
** sata cable
** fsck on the partition
** badblocks - a disk checking tool
** flaky power supply
** flaky GPU card

Did you recently apply any patches that could be related?  Can you restore from a pre-patch backup?
Did you recently change the GPU drivers? Can you go back to the prior version?

---

### Post by RogerDavis on 2013-10-13
1) About a dozen times
2) From the Ubuntu programs list?  Or another place? - I tried another one, but not good results.  Please advise.
3) In process of checking hardware

---

### Post by TheFu on 2013-10-13
The hardware issue can probably be more easily determined by running off a live CD/flash drive with Gnome. If it works as expected, that leads us to think about a corrupt HDD, sata cable, or disk controller, correct? It eliminates other components.

Synaptic will let you see a list of installed packages - find those with gnome inside - select them each to be reinstalled. I would NOT remove and install - use the "reinstall" option.

---

### Post by RogerDavis on 2013-10-13
I will follow the reinstall option.

I have a second user set up on the system, using Unity.  It works, as far as I can tell, ok.

Also, I boot to Windoze 7 from another hard drive (mechanically switched).  Windoze works ok.

Also, some function has returned to my user login, but things are still goofy, with some display artifacts - little spots on the screen on the lower side, sometimes a set of lines in a squarish area at the top left.  I've tried reloading the display driver, some improvement but left the above described artifacts.

This kinda leaves it to software... ?

---

### Post by TheFu on 2013-10-14
> **RogerDavis said:**
> I will follow the reinstall option.

I have a second user set up on the system, using Unity.  It works, as far as I can tell, ok.

Also, I boot to Windoze 7 from another hard drive (mechanically switched).  Windoze works ok.

Also, some function has returned to my user login, but things are still goofy, with some display artifacts - little spots on the screen on the lower side, sometimes a set of lines in a squarish area at the top left.  I've tried reloading the display driver, some improvement but left the above described artifacts.

This kinda leaves it to software... ?

With Windows on a different drive, we cannot rule out anything in the HDD chain - so the controller, sata cable and disk are still suspect.
With the 2nd login working, that DOES rule out the controller and cable, but not specific sectors of the HDD.
Last, reloading the display driver is probably a good idea in this situation, but generally, it is NOT good to be on the latest version under Linux. If things are working with the current driver, don't screw it up.

Newer != better.

Can you run **badblocks** on the Ubuntu partition? This is usually an overnight thing.
I'd try to reinstall all the gnome-* stuff first, but running badblocks in test mode is always a good thing to get the "lazy bits" recognized.

---

### Post by RogerDavis on 2013-10-14
I ran badblocks, no errors.  Apparently same for forcefsck (I see "checking" and no result output), and Smart says all is good.

I'm getting things back, piece by piece, I think mostly due to LOTS of fooling around with Compiz and some Google work and searching on here.  The display aberrations seem to be gone now, the upper and lower bars seem to be behaving (I think), but I can't get the following to work right yet:

1) Switcher - used to be small icons, now huge with semitransparent displays of icons or open pages with small icons.  I prefer small icons only, or at least less transparency.

2) Go to Desktop - Won't go straight to desktop, but instead to a previously open screen, click it again and then desktop.

---

