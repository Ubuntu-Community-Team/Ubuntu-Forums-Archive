---
title: "Control Clicking Fails in Nautilus"
date: 2007-02-16
forum: Desktop Environments
---

### Post by ophion on 2007-02-16
Holding the Control key and left clicking on the mouse to select multiple files does nothing in Nautilus.  What could cause this?

----

Control key click selection was broken almost everywhere (gFTP, media players, etc.).  That helped me narrow it down.  The discussion at the URL below helped me troubleshoot the problem, which turned out to be the Move Window Key setting in System->Preferences->Windows.  Why would a setting that breaks nearly every program be the default?  Is this a bug?

[http://gnomesupport.org/forums/viewtopic.php?t=10827](http://gnomesupport.org/forums/viewtopic.php?t=10827)

By the way, one must close and reopen a window for the new setting to take effect.

---

### Post by ophion on 2007-02-16
So, is it a bug?

---

### Post by warjowuch on 2007-04-15
Same problem here! Somebody a solution? I'll take a look in the gconf...

---

### Post by ComplexNumber on 2007-04-15
works perfectly fine for me, and always has.

---

### Post by warjowuch on 2007-04-17
Good for you :-)
But is someone able to contribute a solution for this? Exploring Gconf-settings did not make it clear for me...
It is really stupid and makes gnome a lot less usable :-(

---

### Post by warjowuch on 2007-04-17
Whoops, the solution was simpler then I thought...
It was indeed the solution in the first post (I thought I did not have that option).

So, it works fine again, thanks!

---

