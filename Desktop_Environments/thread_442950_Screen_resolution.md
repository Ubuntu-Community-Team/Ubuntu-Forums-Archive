---
title: "Screen resolution"
date: 2007-05-14
forum: Desktop Environments
---

### Post by deltarho on 2007-05-14
Using xdpyinfo | grep resolution > 105x106 dots per inch
Using xdpyinfo | grep dimensions > 1280x960 pixels (310x231 millimetres)

Now, 1280*25.4/105 = 309.64 & 960*25.4/106 = 230.04

No problems there but I want 96dpi.

However, putting

#       DisplaySize    338    254    # 1280x960 96dpi

into the "Monitor" Section of xorg.conf and rebooting has no effect.

I have read one reference to the reading of 'DisplaySize' being broken in 7.04.

Is there a workaround?

---

### Post by jfinkels on 2007-05-14
> **deltarho said:**
> Using xdpyinfo | grep resolution > 105x106 dots per inch
Using xdpyinfo | grep dimensions > 1280x960 pixels (310x231 millimetres)

Now, 1280*25.4/105 = 309.64 & 960*25.4/106 = 230.04

No problems there but I want 96dpi.

However, putting

#       DisplaySize    338    254    # 1280x960 96dpi

into the "Monitor" Section of xorg.conf and rebooting has no effect.

I have read one reference to the reading of 'DisplaySize' being broken in 7.04.

Is there a workaround?

I don't know anything about this problem, but...did you put in
```
#       DisplaySize    338    254    # 1280x960 96dpi
```
or did you put in this?```
       DisplaySize    338    254    # 1280x960 96dpi
```(no # in front)?

Any line starting with a # is 'comment' and so is not read at all by the X server!

---

### Post by deltarho on 2007-05-14
Apologies, I copied from a list - the # was actually removed.

---

### Post by deltarho on 2007-05-14
Looks like the 310x231 is hard wired.

So, with X = 310x96/25.4 > 1171 & Y = 231x96/25.4 > 873

Using System>Preferences>Screen Resolution and choosing 1152x864 then

dimensions:    1152x864 pixels (310x231 millimetres)
resolution:      94x95 dots per inch

I will settle on that. :)

---

