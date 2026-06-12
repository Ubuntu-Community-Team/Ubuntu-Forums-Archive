---
title: "xscreensaver keeps crashing my comp"
date: 2005-11-04
forum: Desktop Environments
---

### Post by jamesford on 2005-11-04
im a bit fed up with xscreensaver cos it keeps crashing my machine. not every time but maybe 2 out of 3 times i leave the computer alone for a bit and i get back its crashed. im pretty sure its down to xscreensaver cos if i disable screensaver althogether it never happens.

i uninstalled and reinstalled xscreensaver and things were ok for 2-3 days and now its back crashing the computer again.

so i tried gnome-screensaver instead but it doesent seem to have any power management capabilities. ive got  an LCD screen so the screensaver itself isnt important to me but i want the monitor to be shut off after x minutes.

is there a way to make the monitor turn off after X minutes without using xscreensaver and if so how?

can i uninstall xscreensavevr altogether?

---

### Post by Ampersand on 2005-11-04
If your problem is anything like mine was, uninstalling the 'laptop-mode' package should solve it.

Does setting the screensaver mode to 'disable screensaver', then enabling power management on the advanced tab work (in screensaver prefences)?

---

### Post by gt24 on 2005-11-04
xscreensaver...  Go into xscreensaver, and start going through each and every screensaver and preview them.  I'd say that half of the screensavers slow my system down to a crawl, and a few (2-3 of them) nearly crash my system, and that is just in preview mode!!  So, what I say is that you might want to go through xscreensaver and choose screensavers you like and have previewed before and uncheck the rest.  When you have your screensaver list down to a few proven screensavers (or simply have it run one screensaver), then you might solve your crashing problem...

or at the very least, it is an attempt at solving the problem

---

### Post by jamesford on 2005-11-04
thanks both. this has ntohing to do with what screensaver i use, im always careful to choose a lightweight one that hardly uses cpu at all.  i dont think disabling screensaver but enable power management is going to help, cos i dont think its the screensavers themselves but the whole xscreensaver daemon (or wahtever its called) that causes the problems, i mean the thing that turns the monitor off after x minutes is the thing crashing the computer..i think.

uninstalling laptop-mode also uninstalls acpi-support, powermanagement-interface and ubuntu-desktop....i shouldnt uninstall those should i ?

---

### Post by strawman on 2005-11-25
As far as turning off your monitor after X minutes without xscreensaver, i think it can be done in your xorg.conf file.  Take a look at the man page for xorg.conf, i think it's under the Server Flags section, Option "BlankTime" "time" in minutes.

---

### Post by hoodwink on 2005-11-25
I've gotten very mixed results with xscreensaver on ubuntu, and I'm not sure why. It's rock solid on CentOS (RHEL4 derivative). For a long time it didn't work at all on Kubuntu, but recently I find it working again. No clue why.

Go figure.

---

