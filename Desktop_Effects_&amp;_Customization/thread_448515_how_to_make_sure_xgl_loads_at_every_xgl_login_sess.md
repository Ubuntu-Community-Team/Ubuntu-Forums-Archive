---
title: "how to make sure xgl loads at every xgl login session?"
date: 2007-05-19
forum: Desktop Effects &amp; Customization
---

### Post by adarkenigma on 2007-05-19
i have followed the guide on berly wiki and installed it .. it works fine sometime ... but doesnt work at every login. i.e. even when i have selected xgl session.  i think beryl loads at every xgl login session, since i see the tray icon .. but i have no beryl effects.. also every now and then i get "trash applet" and "gnome applet" right in middle of the screen when i login to xgl session. and i have hit close from gnome panel. and four boxed at right bottom disappears.. same thing happens when close trash applet. anyway's that is not biggest issue. here is my xgl start up script 

```
#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4  
export DISPLAY=:1 
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec /etc/X11/Xsession gnome-session
``` 

what can i do to make sure that xgl loads at every xgl login session? 

any help is much appreciated.

---

### Post by strumluff on 2007-05-19
Hey try changing that startup script to this, it should load XGL properly, and as long as your gdm session option is set up correctly to run this script then you shouldn't have any problems:
```

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session

```
Note: You may also need to install beryl-dbus if not installed on your system by default.

---

### Post by adarkenigma on 2007-05-19
sorry .. but that script doesn't load xgl .. it seems with that script ... every time i login .. nothin happens.. atleast old one loaded xgl some times.. and yes dbus is installed.

---

### Post by adarkenigma on 2007-05-21
anyone ?

---

### Post by jocko on 2007-05-21
Are you sure the problem is that xgl doesn't load?
I have a very similar problem.
Most times when gnome starts in my xgl session I'm getting no decorations or effects (or if I set up beryl-manager to start metacity as backup window manager I'm getting plain metacity).
But xgl is running and if I start beryl from beryl-manager it usually loads fine.
So at least for me the problem is with beryl and not with xgl.
I think if xgl would fail to load you would just be thrown back to the login screen without any attempt to load gnome (from the script xgl is executed before gnome-session, so if xgl fails nothing more will be done).

So next time when gnome loads without effects, check if you can start beryl from beryl-manager (right click the tray icon, make sure beryl is set as window manager and click "restart window manager").
If that starts beryl the problem is that beryl is not entirely stable.
You can also check if xgl is running in the system monitor.

---

