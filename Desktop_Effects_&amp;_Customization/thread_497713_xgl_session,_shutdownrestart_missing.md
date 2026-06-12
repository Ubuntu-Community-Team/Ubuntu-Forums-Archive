---
title: "xgl session, shutdown/restart missing"
date: 2007-07-10
forum: Desktop Effects &amp; Customization
---

### Post by elquer on 2007-07-10
Ubuntu 7.04 64bit ati radeon xpress 200m

i enabled the desktop effects and got it to work on xgl session, but after i restarted i noticed that i only had one workspace and when i tried to restart i couldn't because the restart shutdown buttons were missing. 

i've read everything on the topic but couldn't find anything that could help,

---

### Post by haden9 on 2007-07-12
From this website: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL#IMPORTANT_PLEASE_READ_BEFORE_BEGINNING](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL#IMPORTANT_PLEASE_READ_BEFORE_BEGINNING)

The startup script: Use your favorite text editor to create a script startxgl.sh in your path, like so:

$ sudo gedit /usr/local/bin/startxgl.sh

Shutdown and reboot buttons in GNOME (you need to add this to the startxgl.sh)

#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4  
export DISPLAY=:1 
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec gnome-session

---

### Post by kori.mendocino on 2007-07-12
Try editing your xgl session file (presumably /usr/local/bin/startxgl.sh) and pasting this code over the existing one, then log out and log in again.

```
#!/bin/sh
Xgl :1 -fullscreen -ac -br -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
```

---

