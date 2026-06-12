---
title: "Xubuntu 13.04. - two issues with mounting of external media / digicam"
date: 2013-07-03
forum: Desktop Environments
---

### Post by night-wing on 2013-07-03
Hello.

I use xubuntu 13.04. on my thinkpad x60 and it's great and fast :D

I only have two issues, which only occur in xfce, not in gnome (I tried ubuntu to compare):
My sdcard, which always is in the slot and on which my music mp3 collection is, isn't mounted
after boot. In gnome, it is...
Also my digicam (ixus) isn't active and the gthumb import dialog will not appear, when it's
connected. In gnome, this works...

When I mount both manually or double-click on the drives on desktop, everything works.
Both drives are shown on the desktop always, but they're "greyed" when not mounted.

Is there a hint for me to make this work like in gnome?

Regards
nightwing

---

### Post by slickymaster on 2013-07-03
This behavior is neither xfce nor thunar-specific, it affects all file-managers that employ gvfs.

Just add them to your **/etc/fstab** file, and they will be mounted at boot. See this on how to do it: [Mount/USB]("https://help.ubuntu.com/community/Mount/USB")

---

### Post by night-wing on 2013-07-03
Hello.
Thanks for your post.
Is there another chance to get rid of this problem?
In nautilus, this works without fstab and fstab - entries will affect only these both drives and may cause problems when they're not connected.
Regards
nightwing

---

### Post by cwsnyder on 2013-07-03
You could always install Nautilus and dependencies in your Xubuntu installation.

---

### Post by slickymaster on 2013-07-03
> **cwsnyder said:**
> You could always install Nautilus and dependencies in your Xubuntu installation.

+1.
That would be the simple and easier solution.

---

### Post by night-wing on 2013-07-04
Hello.
Thanks for your posts.
I've found something in a german forum wiki : [http://wiki.ubuntuusers.de/Automount](http://wiki.ubuntuusers.de/Automount)
They wrote about mounting with gvfs-mount, but this doesn't work for me, because
I got an error.
Regards
nightwing

---

