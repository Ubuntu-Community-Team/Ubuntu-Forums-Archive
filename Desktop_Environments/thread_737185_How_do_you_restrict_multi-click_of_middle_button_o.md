---
title: "How do you restrict multi-click of middle button of mouse?"
date: 2008-03-27
forum: Desktop Environments
---

### Post by jis on 2008-03-27
My mouse's (A4 Tech NB-30) middle button is very sensitive. When I press it, it usually results two or three clicks, not just one. Is there way to restrict middle click so that it does not take several clicks in short time to avoid unwanted extra actions?

---

### Post by markjensen on 2008-03-27
I see that touchpads have an "Option    MaxTapTime" that can be set, but it doesn't look like it applies to mice.   It might work.  It might not.

You can try adding it with a value for testing (no, I don't know good values, but a 0 apparently disables taps on a touchpad).   If you try it, make a backup of your current xorg.conf file first.  Then you can get into a TTY login to change it if it disables your mouse.  If you can make it disable the mouse clicks with 0, then you might be able to set it to other values (msecs?) to find a workable point.

If this doesn't work, sorry :(

---

### Post by jis on 2008-03-27
Double-tapping touchpad equals clicking left mouse button so I think it would not affect to the middle button behavior, but I am going to investigate the problem. BTW I have not set MaxTapTime in xorg.conf and tapping does not work, so I think there is another way to configure touchpad.

---

### Post by markjensen on 2008-03-28
Well, the only _true_ way to deal with a hardware problem is to address the hardware...

If the problem is the microswitch for the middle button, then it may have some contamination in it, and electrical contact cleaner (one that doesn't leave a residue) might clean it out nicely.   If the problem is spring force, you might be able to bend the spring to make it more or less forecful.

---

### Post by jis on 2008-03-30
I think the problem is design problem with the mouse. I wouldn't have bought one, if I had known it has this feature. It is most annoying with Firefox.

It would be nice if there was a way to configure the sensitiveness for double-middle-clicking like for normal double-clicking.

---

