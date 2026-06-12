---
title: "Where does gnome-keyboard-properties get its layouts?"
date: 2008-12-22
forum: Desktop Environments
---

### Post by StijnVermeeren on 2008-12-22
I am trying to add a custom keyboard layout to the list in gnome-keyboard-properties. I am roughly following the tutorial on [this webpage]("http://hektor.umcs.lublin.pl/~mikosmul/computing/articles/custom-keyboard-layouts-xkb.html").

I edited the file /etc/X11/xkb/base.xml. The files /usr/share/X11/xkb/rules/base.xml, /usr/share/X11/xkb/rules/xorg.xml and /usr/share/X11/xkb/rules/xfree86.xml all symlink to this /etc/X11/xkb/base.xml.
I would guess that gnome-keyboard-properties gets it's list of layouts there, but this did not work. I even removed the file, restarted X, and gnome-keyboard-properties still had the same list of keyboard layouts.

So where does gnome-keyboard-properties gets it's keyboard layouts, and how can I get my own custom layout to it?

---

### Post by StijnVermeeren on 2008-12-22
[This bug report]("https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/297428") helped me out. It's working now.

---

### Post by jay li on 2008-12-22
Wow, slow down before you'll mow your system. 
All you have to do is just to go to your "System" menu then "Preferences" and then to "Keyboard". 

Now, select the "Layout" tab then press "+" (or "Add") choose what you want and that's it.

---

### Post by StijnVermeeren on 2008-12-23
No, I don't want any keyboard layout that is already in the "Keyboard Preferences" list. I made some of my own modification ("Belgian keyboard with Czech characters") and want to be able to select my own layout in gnome. Which is working now.

---

### Post by jay li on 2008-12-23
So how did you do it?

---

### Post by StijnVermeeren on 2008-12-23
In /usr/share/X11/xkb/rules/evdev.xml I could add the new layout and that worked. See also the [bug report]("https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/297428") I linked in my post above.

---

