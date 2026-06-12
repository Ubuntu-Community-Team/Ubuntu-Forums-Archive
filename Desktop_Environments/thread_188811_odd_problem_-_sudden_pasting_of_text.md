---
title: "odd problem - sudden pasting of text"
date: 2006-06-04
forum: Desktop Environments
---

### Post by justinflavin on 2006-06-04
sometimes when i am posting to these forums (and elsewhere), suddenly text would be pasted into my post, as if its coming from a clipboard somewhere.

i'm using a laptop with a touchpad (maybe thats something to do with it).

its hard to reproduce this one exactly - maybe i'm inadvertently pressing a CTRL key combination by accident?  

anyone else notice this happening?

---

### Post by simplyw00x on 2006-06-04
If you're somehow triggering a middle-mouse button press then that pastes the contents of the secondary clipboard. Shift+Ins also does this I believe.

---

### Post by Feanor on 2006-06-04
It happens also to me sometimes, it depends on tapping i think. I've adjusted sensitivity of the touch pad and now it doesn't happens anymore

---

### Post by netron on 2006-06-05
[QUOTE=Feanor]It happens also to me sometimes, it depends on tapping i think. I've adjusted sensitivity of the touch pad and now it doesn't happens anymore[/QUOTE]

i had a similar problem on my laptop , but i just turned mouse tapping off in xorg.conf, by adding  MaxTapTime and setting it to zero


/etc/X11/xorg.conf:

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
       **Option          "MaxTapTime"          "0"**
EndSection

---

