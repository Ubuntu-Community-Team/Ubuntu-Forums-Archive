---
title: "Upgrade to 14.04 wipes out Gnome?"
date: 2014-04-27
forum: Desktop Environments
---

### Post by redpenguinmail on 2014-04-27
I recently upgraded from 13.10 to Ubuntu 14.04 overnight.

I was happily using Gnome Fallback from various versions of Ubuntu over time. I believe I may have started around Ubuntu 12.04 on this PC.

Anyway, for some reason my username, no matter what session I try and tell it, "Gnome Classic (Compiz)" or "Gnome Classic (Metacity)" it just puts me into a Unity session each time.

I decided to also give MATE a try but even when I try that session, it still does Unity.

Though for some reason if you try "Guest Access", any GUI that you desire can come up.

I have a feeling it's probably a corrupt pref file somewhere but I don't want to go touching random files and break more.

---

### Post by TheFu on 2014-04-27
14.10 will be released in October. You'll need to wait. 14.04 is available now.

All settings are in ~/.config .... if you don't want them to be around, move that directory to any different name, logout, login.  For other DEs to work, those will need to be installed. I cannot speak for any of the choices listed above, but if you install "lxde" and select that at the login screen, it does work.

---

### Post by redpenguinmail on 2014-04-27
> **TheFu said:**
> 14.10 will be released in October. You'll need to wait. 14.04 is available now.

All settings are in ~/.config .... if you don't want them to be around, move that directory to any different name, logout, login.  For other DEs to work, those will need to be installed. I cannot speak for any of the choices listed above, but if you install "lxde" and select that at the login screen, it does work.

LoL, I didn't even realize I said 14.10 but corrected now.

Thanks again for the info.

---

### Post by kansasnoob on 2014-04-28
Possibly this bug:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1232299](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1232299)

A fix is pending in proposed now:

> compiz (1:0.9.11+14.04.20140423-0ubuntu1) trusty; urgency=low

  [ Ryan Tandy ]
 [B] * Fix gnome-flashback session starting Unity plugins. Change the
    profile back after processing settings upgrades. When changing
    profile, discard existing GSettings wrappers pointing to the old
    profile. (LP: #1232299)[/B]

  [ Chris Townsend ]
  * Remove the Number of Desktops option in CCSM as this option confuses
    Compiz and is really no longer needed since the Horizontal/Vertical
    Virtual Desktop Size is what is used for determining the size. (LP:
    #1289820)
  * Due to some change in Gtk SpinButton, setting the initial value in
    Adjustment does not work for integers, so now just explicitly set
    the value after the SpinButton is created. (LP: #1294341)

 -- Ubuntu daily release <ps-jenkins@lists.canonical.com>  Wed, 23 Apr 2014 14:56:06 +0000

---

### Post by outofthecave on 2014-05-01
It's not a Compiz problem.  I have the same issue using Metacity.  And since I don't have Unity installed, I get to a screen showing only my desktop wallpaper, with no gnome panel, no shortcuts working, no reaction to clicking or right-clicking.  I'm using gdm.

---

### Post by fkkroundabout on 2014-05-01
fresh install only, i think is the best way

---

