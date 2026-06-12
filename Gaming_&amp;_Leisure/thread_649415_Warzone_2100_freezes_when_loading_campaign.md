---
title: "Warzone 2100 freezes when loading campaign"
date: 2007-12-24
forum: Gaming &amp; Leisure
---

### Post by stir-crazy on 2007-12-24
Hi all,

first post, very new to Kubuntu (Linux in general), very much enjoying exploring how everything works.  For the most part, Gutsy Gibbon (Kubuntu 7.10) has been very cooperative.

However, installed Warzone 2100, been having a lot of fun, great game, but if I try to load a saved campaign, I get one of two results:

1)  Warzone 2100 simply kills itself, and the top left quadrant of my desktop is zoomed to fill my entire screen.

2)  The WZ 2100 splash screen shows, and then freezes.

Either way, the only fix I've found is to log out, restart the X server (seems the way to get the display corrected), then log back in.

Anybody have any idea what I can do?  There's no debugging info available when this happens.  I'd like to be able to save and load this game!

Thanks in advance!

Unsure if this is of any help, but when I run lspci in Terminal, I get:

```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Proces
sor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Exp
ress Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Gr
aphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High
 Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Ex                                                                                                   press Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Ex                                                                                                   press Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US                                                                                                   B UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US                                                                                                   B UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US                                                                                                   B UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US                                                                                                   B UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US                                                                                                   B2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev                                                                                                    03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE                                                                                                    Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/                                                                                                   b/g PCI Express Transceiver (rev 02)

```

---

### Post by Perfect Storm on 2007-12-25
How did you install warzone and where.

---

### Post by stir-crazy on 2007-12-25
Simply by using Adept_Installer, from the add/remove programs in the K Menu.

I'm not nearly knowledgeable to know how to depackage programs correctly,

So:

K Menu

  add/remove programs

    games tab

      selected Warzone 2100

Let Adept_Installer install the selected items, and that was it.

---

### Post by Perfect Storm on 2007-12-26
Uninstall warzone2100 and try with the latest: [http://wz2100.net/downloads](http://wz2100.net/downloads) and see if it's a bug that have been fix (if it's a warzone2100 bug). The one in the repo is a 2.1 SVN version which means they taken the development version and it can contains bugs and quarks.

---

### Post by stir-crazy on 2007-12-26
Cool, thanks.  Giving that a shot now.  I initially tried the 2.0.9 version (latest Linux version, packaged under MojoSetup, Debian installer not available), which started Wine (?!)...nothing really happened.

I did go back to previous versions, downloaded an Ubuntu specific version, so will try that, see if it's a fix.  

Thanks for the help!  Will post later with an update.

EDIT:

Hmmm....the Ubuntu package failed.  Got the following:

```
Selecting previously deselected package warzone2100.
(Reading database ... 101068 files and directories currently installed.)
Unpacking warzone2100 (from .../warzone2100_2.0.7-0_i386.deb) ...
dpkg: error processing /home/stir-crazy/Desktop/warzone2100_2.0.7-0_i386.deb (--install):
 trying to overwrite `/usr/share/games/warzone2100/warzone.wz', which is also in package warzone2100-data
Errors were encountered while processing: 
 /home/stir-crazy/Desktop/warzone2100_2.0.7-0_i386.deb
```

I assume I need this Mojosetup to decompile the 2.0.9 version then?  Can't seem to find a download for it.

Sorry, I'm sure this is probably obvious...I'm too much of a newbie yet.


EDIT:  I did manage to uninstall and reinstall version 2.0.7, but it seems to suffer the same problem as the 2.1.0 with crashing upon loading a game.  Never figured out how to get the 2.0.9 to work, guess the mojo aint happening for me tonight.

---

### Post by HTML-insane on 2008-02-05
You're getting the same problem as me.
Wine is the Windows Emulator, lets you run (some) windows applications in Kubuntu.
However, you might want to try the Debian package. I am now...

Well, the Debian package didn't work for me. Maybe it's just something I'm doing wrong...

---

### Post by tpischke on 2008-03-04
Deleting the .warzone2100-2.1config file before starting warzone fixes the crash for me.  Must be done before every start.

---

### Post by stir-crazy on 2008-03-05
> **tpischke said:**
> Deleting the .warzone2100-2.1config file before starting warzone fixes the crash for me.  Must be done before every start.

Strange.  Tried that, didn't do anything for me. :(

---

### Post by linuxskeptic on 2008-03-22
I problems with the warzone version in the ubuntu repository too. Uninstalled it, then downloaded warzone2100-2.0.10.mojo from wz2100.net (Linux Installer), to the desktop. Right clicked on it -> Properties -> Permissions -> Enabled "Allow execute file as program". Ran the .mojo file. Then using Synaptic manager installed the latest libphysfs and libSDL_net packages. Now it runs, saves, and loads!

---

