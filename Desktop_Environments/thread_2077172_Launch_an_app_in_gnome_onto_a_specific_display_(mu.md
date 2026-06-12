---
title: "Launch an app in gnome onto a specific display (multi-monitor)"
date: 2012-10-27
forum: Desktop Environments
---

### Post by kerryhall on 2012-10-27
I'm trying to launch an application on to a specific display. Yes, I know it's *supposed* to launch onto whatever window I have my mouse, but this doesn't happen. :)

Doing:
$ DISPLAY=":0.0" gnome-calculator

launches the application fine, but any other numbers besides "0"s there causes an error, eg, 

(gnome-calculator:4211): Gtk-WARNING **: cannot open display: :1.0

Any ideas what the syntax is supposed to be for the $DISPLAY variable?

More info:
Nvidia cards, three displays, gnome not unity. 

A snippet from xorg.conf that may be relevant:
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 1920 0
    Screen      1  "Screen1" 0 0
    Screen      2  "Screen2" 3840 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "1"
EndSection


Thanks!

---

### Post by kerryhall on 2012-11-07
Bump

---

### Post by kerryhall on 2012-12-23
Bump. I realize now that the title is inaccurate. It should work for any window manager, right? Not just metacity? Still having this issue though.

Thanks!

---

