---
title: "Garbled menu fonts?"
date: 2005-10-03
forum: Desktop Environments
---

### Post by nathanf on 2005-10-03
Ever since I got a new monitor, my menu fonts in certain programs like XMMS and MPlayer are completely unreadable.  I've searched all over, and I cannot find a solution to this problem.  help me!

---

### Post by SilentCacophony on 2005-10-03
Have you tried doing this:

**sudo dpkg-reconfigure xserver-xorg**

That'll start a guided reconfiguration for your */etc/X11/xorg.conf* file, and hopefully straighten it out. Generally anytime you change hardware, be mindful that you may make your config file obsolete.

---

### Post by nathanf on 2005-10-07
hmm, now xmms segfaults when i try to open it.  at least I don't have garbled text anymore eh?

---

### Post by 11hjpphty76lkjj on 2005-10-07
Are you using KDE or GDM?

Aaron

---

### Post by nathanf on 2005-10-08
gdm

---

