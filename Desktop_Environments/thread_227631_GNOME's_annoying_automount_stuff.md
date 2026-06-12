---
title: "GNOME's annoying automount stuff"
date: 2006-08-02
forum: Desktop Environments
---

### Post by MM23 on 2006-08-02
Can someone tell me how I can do the following two things?:

1) Stop CDROM, DVDROM, removable USB, and hard drive partitions from automatically mounting in GNOME (I like using the terminal, I used to be a hardcore Gentoo dude so I'm really used to doing 90% of that stuff in mrxvt :o)

2) Stop GNOME from creating an icon on the desktop when I mount them.

It's annoying, and it clutters up my icons. I've looked around and I can't find a setting to disable this.

---

### Post by 5-HT on 2006-08-02
For 1), options are in System -> Preferences -> Removable Drives and Media.
Alternatively, fire up *gconf-editor*, desktop -> gnome -> volume_manager
To disable automounting of hard drives at boot, you'll need to edit /etc/fstab (either comment/remove the relevant entry, or using noauto as an option should do the trick).

For 2), In *gconf-editor, *apps -> nautilus and uncheck Volumes_visible

Hope that helps.

---

