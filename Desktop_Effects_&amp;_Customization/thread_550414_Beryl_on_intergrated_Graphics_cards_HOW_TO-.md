---
title: "Beryl on intergrated Graphics cards HOW TO-"
date: 2007-09-13
forum: Desktop Effects &amp; Customization
---

### Post by acelin on 2007-09-13
Check ATI Driver
In a terminal type:
fglrxinfo

You should see this ouputed on your terminal window:
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series
OpenGL version string: 2.0.6334 (8.34.8)

Install Xgl & Beryl
Add the Beryl repositories to your source list.
In a terminal type:
sudo gedit /etc/apt/sources.list

Add this line to Your Source Lists
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) feisty main
save and close file

Grab the Key for the repository, in a terminal type:
sudo wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -

Update Your System
In a terminal type:
sudo apt-get update

Now install Xgl & Beryl
In a terminal type:
sudo apt-get install xserver-xgl beryl-ubuntu beryl-manager

Setting Up XGL
In a terminal type:
sudo gedit /usr/local/bin/startxgl.sh

and this to the file:
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
save and close file

Then make the xgl script executable by entering this into a terminal:
sudo chmod a+x /usr/local/bin/startxgl.sh

Creating a XGL Login
Make the script, by typing this into a terminal:
sudo gedit /usr/share/xsessions/xgl.desktop

add this text to the file:
[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Comment=Start an Xgl Session
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application
save and close file

Change Your Repository Settings
In a terminal type:
sudo gedit /etc/apt/preferences

Then add this ext to the file
Package: *
Pin: release o=lupine
Pin-Priority: 1000
save and close file

Update Your System
In a terminal type:
sudo apt-get update

Roll Back Beryl-Core
Downgrade beryl- core to a version that works with Xgl
In a terminal type:
sudo apt-get install beryl-core=0.2.0~0beryl1

Now You Just have to Log off and Log into your XGL session and run beryl.

---

