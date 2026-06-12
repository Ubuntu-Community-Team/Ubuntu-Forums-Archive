---
title: "vncserver displays no longer working after upgrade to Jaunty"
date: 2009-05-28
forum: General Help
---

### Post by jerry80234 on 2009-05-28
I have my workstation set up with additional vncserver sessions/displays.  Since upgrading from Hardy via Intrepid to Jaunty the sessions are unusable.  Connecting to the remote desktop "0" session works fine.

The visual effects are set to none.  Below is my xstartup.  This configuration used to work.  Now when I vnc to these sessions, all I get is a grey window with no gnome gui desktop.  Also below is the logfile from the server session.

Any ideas?

xstartup file
#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
unset SESSION_MANAGER
gnome-session &


log
28/05/09 10:40:04 Xvnc version TightVNC-1.3.9
28/05/09 10:40:04 Copyright (C) 2000-2007 TightVNC Group
28/05/09 10:40:04 Copyright (C) 1999 AT&T Laboratories Cambridge
28/05/09 10:40:04 All Rights Reserved.
28/05/09 10:40:04 See [http://www.tightvnc.com/](http://www.tightvnc.com/) for information on TightVNC
28/05/09 10:40:04 Desktop name 'X' (pst-desktop:5)
28/05/09 10:40:04 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
28/05/09 10:40:04 Listening for VNC connections on TCP port 5905
xrdb: No such file or directory
xrdb: can't open file '/home/pst/.Xresources'
Option "--login" is no longer supported in this version of gnome-terminal; you might want to create a profile with the desired setting, and use the new '--profile' option
Xlib:  extension "RANDR" missing on display ":5.0".
Xlib:  extension "Generic Event Extension" missing on display ":5.0".
Xlib:  extension "Generic Event Extension" missing on display ":5.0".
Xlib:  extension "Generic Event Extension" missing on display ":5.0".
Xlib:  extension "RANDR" missing on display ":5.0".
Xlib:  extension "Generic Event Extension" missing on display ":5.0".
Xlib:  extension "Generic Event Extension" missing on display ":5.0".
Xlib:  extension "Generic Event Extension" missing on display ":5.0".
gnome-session[5660]: WARNING: Failed to acquire org.gnome.SessionManager

eom

---

