---
title: "Gnome-pilot &amp; USB"
date: 2005-01-14
forum: General Help
---

### Post by nocturn on 2005-01-14
I have a Sony Clié set up with gnome-pilot and Evolution over USB.
It works flawlessly by itself.

The problems start when I want to use another USB device after syncing (on any port).

It just won't work any more, on my Cardreader the LED goes red (indicating that USB support is down, but it has power).

On Gentoo, I used to have a similar problem, but it was fixed by killing gpilotd after the sync (which released USB).  On Ubuntu, killing (even -9) does not work (the process remains).

Only a reboot gets my system back to use (everything remains working after syncing, but if I plug in another device after that, the systems still works but won't log out or in or reboot, so reset has to be used).

Is anyone seeing the same problem?

---

### Post by nocturn on 2005-01-25
I've posted a bug on this:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=5857](https://bugzilla.ubuntu.com/show_bug.cgi?id=5857)

---

