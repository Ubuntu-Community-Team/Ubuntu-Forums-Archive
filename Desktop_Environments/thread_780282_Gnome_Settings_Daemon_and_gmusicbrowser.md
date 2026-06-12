---
title: "Gnome Settings Daemon and gmusicbrowser"
date: 2008-05-03
forum: Desktop Environments
---

### Post by Sherlock Holmboy on 2008-05-03
I'm having trouble getting my multimedia keys working with gmusicbrowser. I have all the dependant perl packages installed, but when I go to enable the plugin it tells me:
```

no signal with name 'MediaPlayerKeyPressed' is exported in object '/org/gnome/SettingsDaemon'

```
I tried restarting the the gnome settings daemon and get this:
```

joe@joe-desktop:~$ killall gnome-settings-daemon
joe@joe-desktop:~$ gnome-settings-daemon
** (gnome-settings-daemon:8713): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:8713): WARNING **: Could not acquire name

```
Where do I go from here?

---

### Post by Sherlock Holmboy on 2008-05-07
*bump* Gmusicbrowser was working fine in gusty 32bit, but hasn't since the upgrade to 64bit

---

### Post by Sherlock Holmboy on 2008-05-24
*bump*

---

### Post by Sherlock Holmboy on 2008-06-04
I added the repository from gmusicbrowsers web sit and upgraded from version 0.963 to 0.964 and now everything works:guitar:

---

