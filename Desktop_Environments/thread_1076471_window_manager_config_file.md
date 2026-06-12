---
title: "window manager config file"
date: 2009-02-21
forum: Desktop Environments
---

### Post by Sonybuntu on 2009-02-21
I have this problem. My video card doesn't handle compiz very well and so when i switched to it all i got was a white screen.
now when i login, my desktop shows up for about 2 seconds then the white screen shows up. i can access my linux partition from windows and so is there a file i can edit in windows so that the default window manager is gtk?

EDIT: Please disregard this. I got a new PC and I'm loving compiz :D

---

### Post by linuxisevolution on 2009-02-21
What window manager are you using? You don't have to boot into windows if you can get to the login screen. When you get to the login screen, select Sessions and select another desktop environment. If you don't see another environment then restart your computer and quickly hit escape when you see the 1----2----3 countdown. Select recovery and hit enter. Go into a root shell and type apt-get install icewm . after that finnishes reboot normally and before logging in select ICEWM from the sessions menu. From there you can boot into Linux and fix your problem ;)

---

### Post by linuxisevolution on 2009-02-21
Did it work? Can you log back in now? You should be able to find the command in Linux to disable compiz. Usually it's like metacity --replace . Good luck to you.

---

### Post by mcduck on 2009-02-21
Press Ctrl-Alt-F2 to get into console, log in and run these commands:
```
gconftool-2 --type string --set /desktop/gnome/applications/window_manager/default "/usr/bin/metacity"
gconftool-2 --type string --set /desktop/gnome/applications/window_manager/current "/usr/bin/metacity"
```
This should set the window manager back to Metacity, thus disabling the desktop effects. After that you should be able to hot Ctrl_Alt-F7 to get back to graphical interface and log in normally.

edit: I'm not actually sure if these keys are used any moe. Gconf-edtor says that they wouldn't be used, but based on the gnome-wm -script that should be handling loading window manager it might be that they are used anyway. You should give this a try, at least.

---

### Post by Sonybuntu on 2009-02-21
Thank you all for your help!
It didn't exacly work, but I made a new user using root.
:popcorn:

---

