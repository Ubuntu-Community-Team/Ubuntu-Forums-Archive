---
title: "&quot;gksudo firestarter&quot; fails"
date: 2006-09-01
forum: Desktop Environments
---

### Post by eyequeue on 2006-09-01
I'm unable to start firestarter using the menu item, so I ran this in a terminal to debug:

$ gksudo firestarter
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:13734): Gtk-WARNING **: cannot open display:
$ 


Why does this not start firestarter?  I also note it does not prompt me for a password.

gksudo and sudo do seem to work properly with everything other than this though.
(No, I didn't recently run sudo, this was just after logging in, a "fresh" try.)

Is there a file I need to rm to "reset" something?


Thanks in advance for any insight on this, I'm stumped.

---

### Post by Nikos_M on 2006-09-01
Maybe this will help you: [http://www.ubuntuforums.org/showthread.php?t=166863&page=2](http://www.ubuntuforums.org/showthread.php?t=166863&page=2)

---

