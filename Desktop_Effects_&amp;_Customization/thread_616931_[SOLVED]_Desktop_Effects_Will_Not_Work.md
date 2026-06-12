---
title: "[SOLVED] Desktop Effects Will Not Work"
date: 2007-11-18
forum: Desktop Effects &amp; Customization
---

### Post by Sam Plamondon on 2007-11-18
I have ATI Radeon X1270 graphics on a Dell Inspiron 1521, and I am running Ubuntu 7.10 "Gutsy Gibbon" Desktop x86 Edition.  My desktop effects will not work.  At first, my screen resolution was wrong (1024x768) and could not be fixed, and I would try to activate desktop effects, but the screen would get all screwy and a "desktop effects can not be activated" message would pop up.  So, I went to System/Administration/Restricted Drivers Manager and (after some tweaking in System/Administration/Software Sources) enabled "ATI accelerated graphics driver".  After restarting my computer, my screen resolution was correct (1280x800).  However, when I go to System/Preferences/Appearance/Visual Effects, and try to change effects from "None" to either "Normal" or "Extra", this message now pops up:

"The Composite extension is not available"

How can I get a "Composite extension", or otherwise get the desktop effects to work?

---

### Post by Sam Plamondon on 2007-11-18
I also found this in the file "/etc/X11/xorg.conf":

Section "Extensions"
	Option		"Composite"	"0"
EndSection

---

### Post by FuturePilot on 2007-11-18
```
gksudo gedit /etc/X11/xorg.conf
```
Go down to where it says

Section "Extensions"
Option "Composite" "0"
EndSection 

And change the 0 to 1.
Save, then logout and log back in. See if that does the trick.

---

### Post by Sam Plamondon on 2007-11-19
I've fixed the problem.  I had to install "xserver-xgl" and then, when I rebooted, Compiz Fusion (desktop effects) was enabled.

---

### Post by hasbaz on 2008-02-07
thanks i had the same problem

---

