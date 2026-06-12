---
title: "Gnome wont start, ubuntu"
date: 2007-03-31
forum: Desktop Environments
---

### Post by blackslash on 2007-03-31
Hey, ive been useing ubuntu for two weeks now. But when I started my computer today,something happend.

First I get the logingscreen, I enter my username and psw. Then i get the default ubuntu-background, the mouse is working, but there is _nothing_ else on the screen. No menues, nothing. The "splash" that shows when loading is not there.

Im useing Ubuntu 64bit.

Anyone got an idea? :)

---

### Post by pwnb0t on 2007-03-31
wow, any other information that you can give at all?
Anything in your logs? (check /var/log/ directory to see if anything shows up in those logs)

Oh, press ctrl+alt+f2 to get you to a CLI (command line interface) login
then cd to /var/log
check out a bunch of those logs with nano or vim:
e.g. 
nano messages
or 
vim Xorg.0.log

---

### Post by blackslash on 2007-03-31
Hey.

Thx for the answer, but after some searching I managed to fix it.

"sudo dpkg-reconfigure gnome-desktop-data
sudo dpkg-reconfigure gnome-control-center
sudo dpkg-reconfigure gnome-menus
sudo dpkg-reconfigure gnome-system-tools
sudo dpkg-reconfigure gnome-applets
sudo dpkg-reconfigure gnome-session"

And it worked :)

Ill get back to this thread with more info if it happens again.

---

