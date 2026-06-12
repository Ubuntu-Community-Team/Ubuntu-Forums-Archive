---
title: "xmodmap problem"
date: 2007-06-13
forum: Desktop Environments
---

### Post by bikmak on 2007-06-13
my XF86Forward/Back, XF86WWW... keys doesn't work

How could i find, where is the xmodmap file, that i need to change for it's working?

xmodmap -e is not the right way for me.

---

### Post by RedSquirrel on 2007-06-14
I generally use ~/.Xmodmap.

Here is a guide that might help:

[http://cweiske.de/howto/xmodmap/allinone.html](http://cweiske.de/howto/xmodmap/allinone.html)

Also, if this is a desktop computer you might be able to use xorg.conf and your keyboard model to setup the keys.

```

Section "InputDevice"
.
.
.
        Option          "XkbModel"      "your_keyboard_model"
.
EndSection

```

---

