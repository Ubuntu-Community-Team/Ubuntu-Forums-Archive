---
title: "hide KDE and Xfce applications in GNOME."
date: 2013-09-15
forum: Desktop Environments
---

### Post by Greek_Fellows on 2013-09-15
Hi!

I've installed GNOME + KDE + Xfce in Ubuntu 12.04 LTS,
and I'm seeing a bunch of KDE and Xfce applications (mostly I see Xfce applications but I believe there are KDE apps among them) when I log into GNOME.

Can I configure GNOME settings to hide KDE and Xfce applications when I log into GNOME?

---

### Post by vasa1 on 2013-09-15
I think you may have to look at individual .desktop files in /usr/share/applications. There, you'll need to **sudo** edit the .desktop files corresponding to the applications you don't want to see adding something like:
```
NotShowIn=GNOME;
```

Of course, you'll back up the relevant file first :)

I'm not sure about this because I don't have more than one Desktop Environment so this is untested advice!

For more reading on the subject of .desktop files, try:
[http://standards.freedesktop.org/desktop-entry-spec/latest/](http://standards.freedesktop.org/desktop-entry-spec/latest/)
[https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)

---

