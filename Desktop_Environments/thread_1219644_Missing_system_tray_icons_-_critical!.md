---
title: "Missing system tray icons - critical!"
date: 2009-07-22
forum: Desktop Environments
---

### Post by prasadbrg on 2009-07-22
Hello everyone,
  I'm running Xubuntu 9.04 on an Compaq Presario 2184 AT notebook with a Celeron processor and 1 Gig of ram. Couple of days back, after a few desktop crashes, the panel icons dissapeared. I deleted the $HOME/.config/xfce4 directory and also the $HOME/.cache/sessions directory. Sure enough, a new panel appeared, but it's missing the very critical system tray icons: network applet, battery monitor applet, update manager applet, besides any application that sends an icon (applet?) to the system tray: Pidgin, Thunderbird, Qjackctl. I did come across [this thread]("http://ubuntuforums.org/showthread.php?t=849487") which seems similar, but really isn't: the "Add New Items" menu which pops up upon right clicking the panel neither contains the 3 'system' applets, nor helps in bringing back the 3 application icons into the system tray. With Pidgin and Qjackctl, the lack of system tray icons is serious enough to make them unusable - and I do need to use them ASAP, so any help would be much appreciated!
Thanks in advance.
Cheers,
Guru

---

### Post by prshah on 2009-07-22
> **prasadbrg said:**
> but it's missing the very critical system tray icons: network applet, battery monitor applet, update manager applet, besides any application that sends an icon (applet?) to the system tray: 

You need to add the "notification area" applet. That will take care of your update manager, pidgin, etc.

The network applet will only appear if the notification applet _and_ gnome-settings-manager is running.

The battery applet will only appear is the notification applet _and_ gnome-power-settings is running.

You can check if these programs are running with```
ps -e | grep -i -E "sett" \| "power"
```

---

### Post by prasadbrg on 2009-07-22
This solved the problem!:D
Thank you!
Cheers,
Guru

---

