---
title: "Getting Enlightment to show up in GDM"
date: 2005-05-26
forum: Desktop Environments
---

### Post by Kyral on 2005-05-26
Stupid question, but I installed Enlightment, and when I went to change sessions on GDM, Enlightment wasn't in the menu. Anyone know why? (I also forgot where GDM keeps its config file :/)

---

### Post by kb00heda on 2005-05-26
I don't know why it didn't turn up, but I had this problem before, following an installation of XFCE. Then I added a file "xfce4.desktop" in the folder

/usr/share/xsessions

to get it to show up as selectable in GDM. What should this file look like? Well, you could have a look at those already present, e.g., my "xfce4.desktop" reads

[Desktop Entry]
Encoding=UTF-8
# The names/descriptions should really be better.
Name=XFCE
Comment=Use this session to run Xfce as your desktop environment.
Exec=startxfce4
Icon=
Type=Application

whereas my fluxbox.desktop looks like

[Desktop Entry]
Encoding=UTF-8
Name=Fluxbox
Comment=Highly configurable and low resource X11 Window manager
Exec=fluxbox
Terminal=False
TryExec=fluxbox
Type=Application
[Window Manager]
SessionManaged=true

Probably the most important lines are the "Exec=startxfce4" and "Exec=fluxbox". I guess you should set it execute Enlightenment instead, but I'm not sure what the executable is. However, I found this

[Desktop Entry]
Encoding=UTF-8
Name=Enlightenment
Comment=This session starts the Enlightenment window manager
Exec=starte16
Icon=
Type=Application

at <www.wplug.org/pipermail/wplug/2005-February/024349.html>, so perhaps it is either this "starte16" or "starte17" (if that is your and also the latest release of Enlightenment). A quick search using "locate" at a terminal ought to answer that.

---

### Post by Kyral on 2005-05-26
Thanks! And the exec is (for me) enlightenment

---

### Post by kb00heda on 2005-05-26
Good! :)

---

