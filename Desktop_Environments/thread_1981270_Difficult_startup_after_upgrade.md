---
title: "Difficult startup after upgrade"
date: 2012-05-16
forum: Desktop Environments
---

### Post by RogerDavis on 2012-05-16
Yesterday I "upgraded" my efax installation from the package manager, from eugenesan.  (Efax had quit working.)  The upgrades only partially completed, then said "recovering".  It seemed to work normally for the rest of the session (didn't try Efax-gtk).  I hibernated the system, then tried to restart later - no go.  I tried 3 times, finally got a screen with a tiny font, gave about 5 choices.  I selected (don't remember words exactly) something like "normal", the first choice.  I also remember that I had to start the network connection manually.  Again, things seemed normal.  I hibernated the system (my usual method of stopping), and again no start, two tries, tiny font, first choice, now running (for now).

I've tried to remove efax and all it's cousins, and got incomplete removals (But icons are gone in the Software center, not on the desktop?!?)  Here's a partial report:
Removing efax ...
Processing triggers for man-db ...
Setting up linux-image-2.6.32-41-generic (2.6.32-41.89) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Failed to symbolic-link /boot/initrd.img-2.6.32-41-generic to initrd.img: File exists
dpkg: error processing linux-image-2.6.32-41-generic (--configure):
 subprocess installed post-installation script returned error exit status 17
Errors were encountered while processing:
 linux-image-2.6.32-41-generic
Setting up linux-image-2.6.32-41-generic (2.6.32-41.89) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Failed to symbolic-link /boot/initrd.img-2.6.32-41-generic to initrd.img: File exists
dpkg: error processing linux-image-2.6.32-41-generic (--configure):
 subprocess installed post-installation script returned error exit status 17


HELP PLEASE!?

---

### Post by tehk on 2012-05-25
subscribe to this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1000423]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1000423") and wait for a fix.

---

