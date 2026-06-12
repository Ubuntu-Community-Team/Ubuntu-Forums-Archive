---
title: "Programs crashing frequently (reproducible)"
date: 2009-04-15
forum: Desktop Environments
---

### Post by jessj on 2009-04-15
Hi all,

Certain programs always crash whenever I try to close them. If I either click the window manager close button or use the program's own exit function the program freezes (i.e. no response to keystrokes or mouse). 

I can drop to the terminal and kill -9 them, but thats getting annoying.

The programs that do this are Enigma, World of Goo, and Battle for Wesnoth. Programs that aren't graphic heavy open and close fine (Firefox, emacs, Rythmbox...).

I'm running 64-bit hardy and have the proprietary nvidia drivers installed.

I have no idea where to start diagnosing this, I looked at /var/logs/Xorg.log, but didn't see any errors or warnings. Any ideas?

---

### Post by Michael.Godawski on 2009-04-15
hi,

try to run the application which cause trouble via the terminal and see if any error are displayed.

---

### Post by jessj on 2009-04-15
No, there are no error messages on the terminal.

---

