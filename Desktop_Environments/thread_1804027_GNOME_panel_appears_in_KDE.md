---
title: "GNOME panel appears in KDE"
date: 2011-07-14
forum: Desktop Environments
---

### Post by ze_iliasgr on 2011-07-14
Hello to everyone!
I am using Ubuntu 11.04 with both GNOME and KDE environments and I like and use both.
I had a problem in GNOME with the skype system tray icon which didn't appear when skype was starting. After reading this article ([http://forum.skype.com/index.php?showtopic=818699](http://forum.skype.com/index.php?showtopic=818699)) I added the "gnome-panel --replace" command to the start up applications. Then everything was working fine.
But when I logged in to KDE I had GNOME panel as well! Which is normal since I the command myself. 
I tried to remove the "gnome-panel --replace" command but then I didn't have the panel when logging in to GNOME!
Do you have any ideas how to solve this???

---

### Post by nidzo732 on 2011-07-14
Try this script, it should restore the default panel settings
[http://www.starryhope.com/downloads/PanelRestore.tar.gz](http://www.starryhope.com/downloads/PanelRestore.tar.gz)

---

### Post by ze_iliasgr on 2011-07-14
I just tried it! and it didn't work...
It messed up my panel actually and I still have GNOME panel in KDE. If I remove the "gnome-panel --replace" command from the start up then I get no GNOME panel when I log in to GNOME and of course Skype icon does not appear! Now, I have to make GNOME panel as it looked before as well!! I forgot to save...
I was trying to find a file where GNOME or KDE stores start up commands for every desktop environment... Do you think this might work?

---

### Post by Krytarik on 2011-07-14
How about adding this line to the concerning .desktop file in "~/.config/autostart"?:
```
OnlyShowIn=GNOME;
```
Greetings.

---

