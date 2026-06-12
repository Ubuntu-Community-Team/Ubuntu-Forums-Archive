---
title: "Desktop Disappeared"
date: 2006-07-11
forum: Desktop Environments
---

### Post by andylei on 2006-07-11
one day, while doing something, i don't recall what, ubuntu locked up, and i was forced to restart the computer via the button on the tower.  after it restarted, and i logged back in, everything worked as usual, except my desktop. everything that was previously on it is no longer there.  it was just empty.  i got my wallpaper back, and that works fine, but all the shortcuts are gone.  the physical files are in my /home/user/Desktop directory, but they don't show up on the desktop.  i also can't add anything new to the desktop by dragging.  i've logged in and out, restarted gnome, and restarted my computer at least six times each, with no results.

i'm using ubuntu 6.06, the 2.6.15-25-k7 kernel, an athlon xp 1800+, and ATi 9600 pro video card.

sorry if the answer has already been addressed, but i tried searching the forums (and google) to no avail.

i'd appreciate any help.  thanks.

---

### Post by aysiu on 2006-07-11
Try going to System > Preferences > Sessions and unchecking the box that says to save sessions automatically at logout.

Then log out and log back in again.

---

### Post by andylei on 2006-07-11
thanks for the reply aysiu.  i've tried logging in and out with the box checked and unchecked, and it doesn't seem to do anything.

---

### Post by Wolki on 2006-07-11
First, try starting nautilus (Alt-F2, "nautilus"), it draws the desktop and maybe it does not get started automatically anymore.
If that does not help, open the gconf editor (Alt-F2, "gconf-editor") and see whether /apps/nautilus/preferences/show_desktop is set. If it is not, check the checkbox.

---

### Post by andylei on 2006-07-11
thanks wolki.  that worked perfectly!

---

