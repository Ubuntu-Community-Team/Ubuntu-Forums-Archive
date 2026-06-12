---
title: "[SOLVED] Taskbar is on the Wrong Screen!"
date: 2007-12-04
forum: Desktop Effects &amp; Customization
---

### Post by dethredic on 2007-12-04
I have two screens set up in twin view, and the taskbar is on the right screen, and I want it on the left one. Any way to change this?

---

### Post by Series8217 on 2007-12-04
What does your xorg.conf look like under Section "Screen"?
On mine I think I added:
    Option "TwinViewXineramaInfoOrder" "DFP"
to make my digital display the primary one.
Alternatively you should be able to just drag the taskbar over to the screen you want it to be on.

---

### Post by dethredic on 2007-12-04
ok, I didn't know I could drag them. Thanks man.

---

