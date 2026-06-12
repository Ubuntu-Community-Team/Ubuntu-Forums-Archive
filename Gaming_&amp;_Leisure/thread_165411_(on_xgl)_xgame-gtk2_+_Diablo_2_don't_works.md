---
title: "(on xgl) xgame-gtk2 + Diablo 2 don't works"
date: 2006-04-24
forum: Gaming &amp; Leisure
---

### Post by Paool on 2006-04-24
Hi. I'm running dapper ang xgl, when I try to run Diablo 2 on cedega with xgame script I got this error... I don't know whats wrong :-k 


Starting Diablo 2...
xauth:  creating new authority file /home/paool/.serverauth.7745

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux korytko 2.6.15-21-386 #1 PREEMPT Fri Apr 21 16:43:33 UTC 2006 i686
Build Date: 16 March 2006
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.94.log", Time: Mon Apr 24 20:59:37 2006
(==) Using config file: "/etc/X11/xorg.conf"

The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
Nie mo&#380;na uzyska&#263; deskryptora pliku wskazuj&#261;cego na konsol&#281;
AUDIT: Mon Apr 24 20:59:40 2006: 7765 X: client 2 rejected from local host
Xlib: connection to ":94.0" refused by server
Xlib: No protocol specified

Traceback (most recent call last):
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 35, in ?
    raise Point2PlayError(_("Unable to load GTK2 Python bindings") + "(%s)" % str( sys.exc_info()[1] ) )
NameError: name '_' is not defined
FreeFontPath: FPE "/usr/share/X11/fonts/misc" refcount is 2, should be 1; fixing.

---

### Post by jon_z on 2006-05-09
its not going to work because you cant run a game that uses 3d when your GPU is being used to render Xgl... Switch back to regular gnome and you can play fine.

---

### Post by Kebabji on 2006-05-16
thats what xgame is for, i can play games like quake iii now because of it - u dont have to swtich back (it opens a new session i believe)

---

