---
title: "Remove devices from unity but still show them elsewhere"
date: 2014-09-24
forum: Desktop Environments
---

### Post by mIXpRo on 2014-09-24
Hi , 
I have a lot of mounted devices , and they take a lot of space in unity launcher , how do i remove them but still have them showing like on the Desktop inside a directory or in the notification bar top like in windows with a drop down menu listing them  ? 
thaks .

Ubuntu 14.04

---

### Post by mc4man on 2014-09-24
To remove from launcher r. click > unlock

As far as available elsewhere - 
On the desktop, if using nautilus, it  is done in bulk from dconf, ex.
```
gsettings set org.gnome.nautilus.desktop volumes-visible true
```
or above with false to remove

As far as elsewhere it can be done thru a link, (a bit of a convoluted process),  but can't see why one would want as the volumes are always  in the nautilus sidebar by default

---

