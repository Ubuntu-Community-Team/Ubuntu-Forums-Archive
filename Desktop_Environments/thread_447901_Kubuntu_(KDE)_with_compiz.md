---
title: "Kubuntu (KDE) with compiz"
date: 2007-05-18
forum: Desktop Environments
---

### Post by Neuralgia on 2007-05-18
Ok, I hope someone can help me out here.

I installed Ubuntu. I have an ATI x300 card. when I use te restricted driver, my desktop effects go away.

Since I liked them so much, and Beryl has too many options, I installed a XGL session. My desktop effects are back :)

After thta, I decided to install Kubuntu desktop.

So no I have this sessions:

1. Gnome
2. Gnome w/ XGL
3. KDE

The question comes here: How can I make a "4. KDE w/ XGL" session

When making a "2. gnome w/XGL" I did this:

> Updated system:
sudo aptitude update
sudo aptitude upgrade

Install XGL:
sudo aptitude install xserver-xgl

Made script and edit it:
sudo gedit /usr/local/bin/startxgl.sh

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session

Made the script executable: 
sudo chmod a+x /usr/local/bin/startxgl.sh

Created a Session called "Gnome w/XGL":
sudo gedit /usr/share/xsessions/xgl.desktop

[Desktop Entry]
Encoding=UTF-8
Name=GNOME with XGL
Comment=
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application

Made this sricpt executable:
sudo chmod a+x /usr/share/xsessions/xgl.desktop


I used [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29) to do this (which is intended to install Beryl, but I just wanted the regular Effects, Beryl is too much for me), so I modified that, so I just got the XGL working, and forgetting about the Beryl part.

Now, the question is:

Which parts do I have to modify, of what I did, so i can get Compiz on KDE session?

I hope I'm not getting too technical here, but I really love both desktops (Gnome and KDE), and like to change once in a while. Without Compiz on KDE, I feel that I'll start to use more Gnome, only for the effects... and that's not fare.

Thanks for the help

Neu

---

