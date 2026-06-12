---
title: "XGL Artifacts"
date: 2006-11-13
forum: Desktop Environments
---

### Post by thrillhouse on 2006-11-13
I recently installed xgl/beryl on my laptop.  I've noticed that there are artifacts around the popups that appear when you hover over the names of programs (see attached screenshot).  Also, when every I get a notication from anything in the "system tray", the whole screen goes green until it goes away.  Any help??  Thanks.

---

### Post by kosmic on 2006-11-13
Edit xorg.conf file (/etc/X11/xorg.conf) and comment out the line that says - Option "XAANoOffscreenPixmaps"

For me it removed the artifacts.

---

### Post by thrillhouse on 2006-11-13
That option wasn't in my xorg.conf file.  They seem to have gone away after move the screen around the cube for a little while.

---

### Post by thrillhouse on 2006-11-13
Also happens when the screen saver goes off.

---

### Post by thrillhouse on 2006-11-14
I can also get it to go away by spining the desktop around the cube, which I assume forces the whole screen to redraw.

---

### Post by cantormath on 2006-11-18
> **thrillhouse said:**
> I can also get it to go away by spining the desktop around the cube, which I assume forces the whole screen to redraw.

Whats your hardware?

---

### Post by cantormath on 2006-11-18
Somebody help this guy.......Im not a XGL expert...
What kind of videocard do you have...?

---

### Post by thrillhouse on 2006-11-18
ATI Radeon Mobility 7500

---

### Post by dresnu on 2006-11-20
You 're not the only one experiencing strange artifacts with a mobility radeon 7500.
Same problem here only with aiglx not xgl. I'll see what happens if I disable that option suggested in a previous post.

---

