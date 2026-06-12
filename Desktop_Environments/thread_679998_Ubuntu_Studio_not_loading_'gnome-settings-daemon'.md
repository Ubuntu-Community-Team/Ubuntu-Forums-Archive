---
title: "Ubuntu Studio not loading 'gnome-settings-daemon'"
date: 2008-01-27
forum: Desktop Environments
---

### Post by mark2 on 2008-01-27
Just did a fresh install this morning, and got this error:

Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.

So i ignored it for the time being, and did the updates that it asked to do some 200mb worth, so i download them, and its still doing it?!

Is there a fix for this? I did the usual search round for other posts bout it, but none had anything about a fix or anything.

PC Specs: P4-HT 2.8Ghz, 1.5Gb RAM, ATI Radeon 9600 Pro 256MB and a Seagate 120g hdd.

---

### Post by MetalMusicAddict on 2008-01-27
This happens sometimes. Happens to me in Ubuntu and Edubuntu. Usually a reboot fixes it. Hasn't happened in Hardy so far. (crosses fingers)

---

### Post by mark2 on 2008-01-27
> **MetalMusicAddict said:**
> This happens sometimes. Happens to me in Ubuntu and Edubuntu. Usually a reboot fixes it. Hasn't happened in Hardy so far. (crosses fingers)

Tried restarting a number of times, as well as fiddling around with the packages, uninstalling and re-installing. Still nothing, so i'm reinstalling normal Ubuntu 7.10 as we speak, atleast i know it works :)

---

### Post by Sandsound on 2008-01-29
> **MetalMusicAddict said:**
> Usually a reboot fixes it.

Restarting x does it for me [ctrl]+[alt]+[backspace]
It might be a small bug, but it's rather annoying.

Is it possible that it have something to do with how and when "gnome-settings-daemon" is loaded ?

---

