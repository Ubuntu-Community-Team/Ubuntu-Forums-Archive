---
title: "difference in these commands if issued in Ubuntu 12.04 ?"
date: 2013-02-23
forum: Desktop Environments
---

### Post by wpshooter on 2013-02-23
Is there any difference in what is accomplished by these 2 commands ?

sudo apt-get install gnome-session-fallback

sudo apt-get install gnome-panel

Thanks.

---

### Post by MG&amp;TL on 2013-02-23
I've never done it, but from what I can tell from [http://packages.ubuntu.com/precise/gnome-session-fallback](http://packages.ubuntu.com/precise/gnome-session-fallback) , *gnome-panel* is (just) the Gnome 2.x panel, whereas *gnome-session-fallback* is the entire session.

---

### Post by tartalo on 2013-02-23
I had a look with "sudo apt-get -s install" (-s means simulate, it doesn't actually install anything) 

Both install exactly the same packages.

EDIT: I must say that I tried in 12.10, not 12.04

---

