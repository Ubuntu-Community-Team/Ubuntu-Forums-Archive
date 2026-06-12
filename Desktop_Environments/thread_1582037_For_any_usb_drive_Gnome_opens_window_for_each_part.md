---
title: "For any usb drive Gnome opens window for each partition"
date: 2010-09-25
forum: Desktop Environments
---

### Post by a271828 on 2010-09-25
For any usb drive Gnome opens window for each partition -- how to disable this?

I am OK if Gnome mounts them. But I would like to have some settings and decide for which drive which partition I would like to mount.

Any ideas how to do this?

Related thing. With google I saw suggestions to use
 gnome-volume-properties

But it is not there any more - Ubuntu 10.04.

---

### Post by asmoore82 on 2010-09-26
If you would still like things mounted but not opened,
Open any file browser window, "Places -> Home" for example,
Then, "Edit -> Preferences"
Then, click the last tab, "Media"
And, un-check the last option "Browse media when inserted"

If you don't want things mounted at all, run this:
```
gconf-editor
```
either in a terminal or "Run Dialog" (Alt+F2 by default)
Then, in the left pane, browse down to /apps/nautilus/preferences
And, in the right pane, slightly less than half way down, un-check "media_automount"
BTW, the "media_automount_open" key directly corresponds to the "Browse media when inserted" option above.

---

