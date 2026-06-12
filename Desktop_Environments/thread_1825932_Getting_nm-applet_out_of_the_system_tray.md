---
title: "Getting nm-applet out of the system tray"
date: 2011-08-16
forum: Desktop Environments
---

### Post by whatthefunk on 2011-08-16
I dont use Network Manager to connect, but the nm-applet wireless icon wont go out of the system tray.  Ive tried to do it through the GUI by unchecking Network Manager in the startup applications: didnt work.  I tried to do it by editing the .desktop files in /.config/autostart and /etc/xdg/autostart: didnt work.  I deleted all the .desktop files: didnt work.  I can get rid of it by killing nm-applet, but then it comes back next time I log in.  Is there any way to get rid of this stupid thing outside of purging Network Manager?

---

### Post by kerry_s on 2011-08-16
Create an auto start to kill it. 
Go to ~/.config/autostart
Open the terminal
Type-> lxshortcut -o kill-nm.desktop
Fill in the info, for command put "killall nm-applet"

---

### Post by whatthefunk on 2011-08-17
Nope.  Still there.

---

### Post by Duncan Williams on 2011-08-17
can you use `startup manager' to switch it of there? (as I can)
[IMG]http://files.myopera.com/DuncanWilliams/usercss/startup-nm.png[/IMG]

---

### Post by wojox on 2011-08-17
Edit:

```
sudo leafpad /etc/xdg/lxsession/Lubuntu/autostart
```

---

### Post by whatthefunk on 2011-08-17
> **wojox said:**
> Edit:

```
sudo leafpad /etc/xdg/lxsession/Lubuntu/autostart
```

Excellent.  I commented out @nm-applet and its gone on reboot.  Thanks wojox and everyone else who tried.

---

