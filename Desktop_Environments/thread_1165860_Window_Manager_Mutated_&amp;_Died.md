---
title: "Window Manager Mutated &amp; Died"
date: 2009-05-21
forum: Desktop Environments
---

### Post by Ravensound on 2009-05-21
My Gutsy laptop window manager mutated and died after I did several mp3 and ogg source install and remove operations.  The wastebasket changed to trash and the windows manager took on a zoom effect, then disappeared (probably after a clean-up).  Comparisons with my Dapper desktop shows four Metacity binaries have gone missing.  If I try to install Metacity I get a Apt removal warning. Can I copy the missing files across or is there another way to recover?

---

### Post by Burillo on 2009-05-21
maybe try reinstalling metapackage ubuntu-desktop / kubuntu-desktop / whatever-buntu-desktop

---

### Post by Ravensound on 2009-05-21
Tried sudo aptitude install ubuntu-desktop and it went through the process ok but did not add or delete any files.

---

### Post by Ravensound on 2009-05-22
I think it may be beyond repair - after using aptitude to install ubuntu desktop, metacity and gnome-panel, metacity works in that it produces a terminal frame, gnome shows the desktop but there's very little else, files are all unknown and there are warnings about the settings daemon restarting too many times.

I've now reloaded the OS, just in case anyone looks at this.

---

