---
title: "Third mouse button emulation"
date: 2009-05-31
forum: General Help
---

### Post by cguy on 2009-05-31
Hi!
Is there a way to enable the third mouse button emulation in Jaunty using a GUI?
I can't find the option in the mouse cofiguration utility of Gnome.

---

### Post by cguy on 2009-06-01
bump

---

### Post by picopir8 on 2009-06-02
I was going to say, add it to xorg.conf, but that file looks like a ghost town these days, no mouse section at all. Though you can still add one if you like.

I did come across this which provides several ways to emulate the third mouse button.
[http://www.pubbs.net/samba/200904/59839/](http://www.pubbs.net/samba/200904/59839/)

---

### Post by dcstar on 2009-06-02
> **cguy said:**
> Hi!
Is there a way to enable the third mouse button emulation in Jaunty using a GUI?
I can't find the option in the mouse cofiguration utility of Gnome.

This works in my xorg.conf for my MS Wireless mouse:

```
Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"
EndSection
```

---

### Post by cguy on 2009-06-04
But no GUI configuration in Gnome, eh?

---

