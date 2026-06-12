---
title: "The 'cube' desktop and touchpad mouse"
date: 2007-09-29
forum: Desktop Effects &amp; Customization
---

### Post by Linicks on 2007-09-29
Hi all,

I turned on the desktop effects, and after a bit of messing, it works really great, and I can't stop using now!

One issue is how can I get my laptop touchpad mouse to work with the Ctrl+Alt key sequence?  All it does at the moment is move the cursor?

Inspiron 6400 pre-installed Ubuntu

```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
#       Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "true"
EndSection
```


BTW, if you can't play videos using the desktop effects (X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0)  try using:

>  mplayer -vo x11 video.avi  (or whatever the video is).

Nick

---

### Post by Linicks on 2007-09-29
OK, ignore this - I was being a dork.

It works fine - I forgot to hold down the 'mouse button' on the pad :lolflag:

Nick

---

### Post by lrdnitecon on 2007-09-29
so you have to hold ctrl+alt+left mouse button and move the cube with your finger?

---

### Post by Rupertronco on 2007-09-29
If you just hit Ctrl+Alt and tap the touchpad it the cube moves with your finger, it's really quite fun to do.

---

### Post by Linicks on 2007-09-30
> **lrdnitecon said:**
> so you have to hold ctrl+alt+left mouse button and move the cube with your finger?

Yes, just use the touchpad mouse button.  You have to be a bit of a contortist to use it though.


> **Rupertronco said:**
> If you just hit Ctrl+Alt and tap the touchpad it the cube moves with your finger, it's really quite fun to do.

I have tapping turned off, so haven't got that option.

Nick

---

