---
title: "KDE 4.2 beta 1 and Google Gadgets?"
date: 2008-12-09
forum: Desktop Environments
---

### Post by CyberAngel on 2008-12-09
Is it possible to use Google Gadgets with plasma using the already created packages for intrepid?

[http://code.google.com/p/google-gadgets-for-linux/wiki/GglWithKDE4Plasma](http://code.google.com/p/google-gadgets-for-linux/wiki/GglWithKDE4Plasma)

---

### Post by CyberAngel on 2009-01-28
Still the same question using the latest stable KDE 4.2 that it has just been released...

---

### Post by adibudeen on 2009-01-28
I've been wondering this too.  There's seems to be no way to add them.

I tried adding a google gadget using the "web widget" option, but it did not work.

In fact, trying to add Mac OS X dashboard widgets gives an error as well.

In both instances, it says "installing the package *such-and-such.zip* failed".

---

### Post by t_k on 2009-01-28
I got this problem too.

Are you people on Kubuntu? 

Only package i could find was google gadget for GTK, and i don't want that. I have no "add google gadget" dialog when i choose install new widgets.

---

### Post by CyberAngel on 2009-01-28
> **adibudeen said:**
> I've been wondering this too.  There's seems to be no way to add them.

I tried adding a google gadget using the "web widget" option, but it did not work.

In fact, trying to add Mac OS X dashboard widgets gives an error as well.

In both instances, it says "installing the package *such-and-such.zip* failed".

I managed to load MAC OS X dashboard widgets but not all of them will work correctly...

---

### Post by Ayuthia on 2009-01-28
I grabbed it from svn, compiled, and installed it.  It does not show up as a plasmoid/applet/widget though.  To use it, I had to execute ggl-qt.

I am using Jaunty though but it should not make a difference if you were able to get the source compiled.

---

### Post by t_k on 2009-01-29
Bump

---

### Post by Ayuthia on 2009-01-29
It doesn't look like it is going to be possible to get it as an applet yet because google-gadgets does not have a stable API/ABI policy yet.  So it looks like if you want it as an applet, you need to compile kdebase.

[http://forum.kde.org/google-gadgets-in-kubuntu-kde-4-2-t-28883.html](http://forum.kde.org/google-gadgets-in-kubuntu-kde-4-2-t-28883.html)

---

