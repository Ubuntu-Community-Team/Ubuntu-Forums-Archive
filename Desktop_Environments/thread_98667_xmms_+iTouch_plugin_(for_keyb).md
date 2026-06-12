---
title: "xmms +iTouch plugin (for keyb)"
date: 2005-12-03
forum: Desktop Environments
---

### Post by [pl]ice on 2005-12-03
hey,
  just installed breezy, and a i can't configure iTouch, when i do the code from keyb. catching, then activate the plug, click ok, xmms shuts down and if i open it, it will open just for a second, then closes. I wiped .xmms tried again etc. no help.
my keyb. is: wless MS multimedia keyb.  it was ok u/d 5.04 ...
thanks

---

### Post by cdoglinux on 2006-08-01
I have the same problem, xmms just crashes after trying to enable the itouch plugin.  I have the Logitec Chordless Comfort Duo for a keyboard.  In a terminal, the error I get is:

Gdk-ERROR **: BadAccess (attempt to access private resource denied)
  serial 8 error_code 10 request_code 33 minor_code 0

From what I gather Gdk is the thing that's messing up.  Aside from re-compiling my own version of Gdk from scratch, I have no idea how to fix this.  Any suggestions?

Chris

---

### Post by [pl]ice on 2006-08-02
which ubuntu do u have? the newest one?? i still haven't figure out the problem :/

---

### Post by cdoglinux on 2006-08-03
I am running Dapper Drake 6.0.6, XMMS 1.2.10, and the itouch package is 0.1.2.  Whenever I go under Options > Preferences, then go to the General tab, and enable the itouch plugin, all of XMMS crashes, and this happens everytime.  That's pretty much the problem.

---

