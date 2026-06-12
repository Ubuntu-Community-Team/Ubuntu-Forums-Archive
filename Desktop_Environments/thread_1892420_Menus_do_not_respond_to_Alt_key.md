---
title: "Menus do not respond to Alt key"
date: 2011-12-07
forum: Desktop Environments
---

### Post by VanillaMozilla on 2011-12-07
<Alt>f should give the File menu, etc., but the menu does not respond in any program, with the exception that <Alt>h activates the Help menu.

This happens in only one account.

<Alt>f1 and <Alt>f2 also work.

What's going on?  I haven't found any preferences yet that affect it.

---

### Post by kurt18947 on 2011-12-08
I just tried all the FireFox alt-letter menu keys and they work properly.  I'm using 11.10 Gnome-shell.  Maybe check which keyboard is selected?

---

### Post by VanillaMozilla on 2011-12-08
I've solved the problem -- sort of.  The problem isn't the wrong keyboard, but I can't really tell what I changed.

The choice of keyboards is a bit of a mess.  There are many (but not enough) combinations of keys in the various keyboards, but there's no obvious way to redefine the various keys.  I have a genuine 101-key IBM keyboard, but that keyboard doesn't seem to be defined.

It turns out that the left <Alt> button worked, but the right one did not.  The right button is defined as an ISO_Lev... button -- whatever that is -- but as it turns out, that's not the problem because it's the same keyboard as in the other account that works.  There must be some different setting somewhere, but I can't find it.

What does work is to press the button and restore the defaults.  That gives you a generic 105-key keyboard with the <Alt> key defined incorrectly, but it works nonetheless.  Go figure.

---

