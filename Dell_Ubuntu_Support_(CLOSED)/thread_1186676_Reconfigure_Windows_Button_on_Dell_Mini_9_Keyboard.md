---
title: "Reconfigure Windows Button on Dell Mini 9 Keyboard for Ubuntu"
date: 2009-06-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by inac on 2009-06-13
Is there a way to remap the keyboard, or to make the windows button on the mini9 keyboard do something in ubuntu?

---

### Post by coffeeaddict22 on 2009-06-13
Hi,
It does get used.  If you see anything referring to the Super key, that's it.  I believe you can get a sticker for it that has a Tux on it if you're feeling keen.
Remapping the keyboard isn't too difficult.  Have a look in System/Preferences/Keyboard first up and check it's picked the right option.  In there click the Layout options key and you can modify the Super key behaviour (among other things).

---

### Post by inac on 2009-06-13
By default, the super key/windows key doesn't seem to do anything on Ubuntu 8.x. Does it just silently activate sudo?

---

### Post by ugm6hr on 2009-06-14
> **inac said:**
> By default, the super key/windows key doesn't seem to do anything on Ubuntu 8.x. Does it just silently activate sudo?

Originally, it activated full-screen mode, but some Dell updates disabled that.

You can use xmodmap to remap it to F11 (which will enable fullscreen mode in Firefox at least, and most Gnome apps).  Can't remember how to do this now, but I'm sure a quick search will find it.

---

