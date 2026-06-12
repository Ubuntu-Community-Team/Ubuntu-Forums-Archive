---
title: "Help need to undo a guide i followed for ATI Compiz!"
date: 2007-09-07
forum: Desktop Effects &amp; Customization
---

### Post by contro on 2007-09-07
[B]I followed this guide...
[http://ubuntuforums.org/showthread.php?t=482773](http://ubuntuforums.org/showthread.php?t=482773)

Following it failed horribly. 
I think the problem lies somewhere here :[/B]

To create the login entry, create a new file /etc/X11/sessions/xgl.desktop
Code:
sudo mkdir -p /etc/X11/sessions
sudo gedit /etc/X11/sessions/xgl.desktop
Make it looks like
Code:
[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application


**Can anyone show me how to undo what i did in that guide** in order to follow this guide

[http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)

[B]and get this to work 

Now copy and paste this into the file that pops up:[/B]

Code:
#!/bin/sh
Xgl :1 -fullscreen -ac -br -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
SAVE THIS FILE! Once its done saving, make that fire executable (like a program) by pasting this into a terminal:

Code:
sudo chmod a+x /usr/local/bin/startxgl.sh
Now we need to make a way to start that session from your login menu, paste this into a terminal:

Code:
sudo gedit /usr/share/xsessions/xgl.desktop
And paste this into the file:

Code:
[Desktop Entry]
Encoding=UTF-8
Name=GNOME with XGL
Comment=
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application
Now make this script executable by pasting this into a terminal:

Code:
sudo chmod a+x /usr/share/xsessions/xgl.desktop

basically I can't start xgl w/ gnome...

---

