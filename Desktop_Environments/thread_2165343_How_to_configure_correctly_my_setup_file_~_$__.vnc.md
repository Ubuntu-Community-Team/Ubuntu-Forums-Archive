---
title: "How to configure correctly my setup file: ~ $ / .vnc / xstartup,"
date: 2013-08-04
forum: Desktop Environments
---

### Post by gameboy709494-d on 2013-08-04
I want to configured correctly my setup file: ~ $ / .vnc / xstartup, otherwise, in my remote desktop connection,  i only to see an "X" mouse cursor could and not see the other things (such desktup icon ,menu etc.)
I hope that through Windows Remote Desktop to remotely control my Ubuntu, but there has been such a problem:


after logging in,  in a dialog "Login to xrdp", select the the "sesman-Xvnc", also enter the correct user name and password, but after clicking OK, it showed me a black fork X mouse, and the desktop background, no anything else, except the host's voices of login and the unlock password dialog (I set the automatic login).


I introduce the situation of my computer:
OS Ubuntu 13.04, the desktop environment is Unity,
Software:
vnc4server 4.1.1   xorg4.3.0-37ubuntu5, automatic
xrdp 0.6.0-1
WinOS: Windows home basic,
Probably so, run vncserver, it generates ~ $ / .vnc / xstartup file as follows:


```

#! / bin / sh


# Uncomment the following two lines for normal desktop:
# Unset SESSION_MANAGER
# Exec / etc/X11/xinit/xinitrc


[-X / etc / vnc / xstartup] && exec / etc / vnc / xstartup
[-R $ HOME / .Xresources] && xrdb $ HOME / .Xresources
xsetroot-solid grey
vncconfig-iconic &
x-terminal-emulator-geometry 80x24  10  10-ls-title "$ VNCDESKTOP Desktop" &
x-window-manager &

```


I actually read a lot about  online information of this file "xstartup", but I  still do not understand the content of the file, followed by each machine are not the same, so to send a topic to see someone understand the file not ~


I need help, who can solve this problem?
(ps:My mother tongue is Chinese, so may be a bit words do not convey.
Ha ha!)

---

