---
title: "[SOLVED] logout freezes computer"
date: 2007-10-03
forum: Desktop Environments
---

### Post by arjones85 on 2007-10-03
7.04 - 

Brand new install, latest restricted ati driver. Clicking on "logout" or "switch user" drops the computer to a black screen, then nothing happens. Something is still happening behind the scenes though because if I press my wireless button on the laptop that works fine, pressing it once turns the light off, pressing it again turns the light back on.

Any idea why logout or switch user is doing nothing but giving me a black screen?

---

### Post by undecidable on 2007-10-04
I think this is a known bug,
see [https://bugs.launchpad.net/ubuntu/+bug/38915](https://bugs.launchpad.net/ubuntu/+bug/38915)

My own experience with it and how to get out of it is in the 4th last post.

A not too complicated workaround is in a post by Michael Mayer
a bit further up,
or you can follow this permallink:
  [https://bugs.launchpad.net/ubuntu/+bug/38915/comments/43](https://bugs.launchpad.net/ubuntu/+bug/38915/comments/43)

Hope this helps.

---

### Post by arjones85 on 2007-10-04
That worked! Just to rehash for anyone that searches for this issue later and stumbles upon this thread, this worked for me  and I am running Gnome:

The following fixed the issue:

sudo vi /etc/X11/gdm/gdm.conf

Scroll down and uncomment and change the line to:

AlwaysRestartServer=true

Fixed!

---

### Post by undecidable on 2007-10-05
Nice to see a problem solved occasionally!

You might mark this thread as 'Resolved'
(see Thread Tools at top)
which might encourage people who have this problem to look in it.

---

### Post by MaximB on 2008-01-21
deleted

---

