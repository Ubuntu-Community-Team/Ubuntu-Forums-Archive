---
title: "XFCE4 on VNC"
date: 2005-05-18
forum: Desktop Environments
---

### Post by sciurus on 2005-05-18
I'm trying to get vncserver to start an XFCE session.

My ~/.vnc/xstartup
> #!/bin/sh
xrdb $HOME/.Xresources
xsetroot -solid grey
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
exec /usr/bin/startxfce4 &

The log for the session
> 18/05/05 22:04:48 Xvnc version 3.3.tight1.2.9
18/05/05 22:04:48 Copyright (C) 1999 AT&T Laboratories Cambridge.
18/05/05 22:04:48 Copyright (C) 2000-2002 Constantin Kaplinsky.
18/05/05 22:04:48 All Rights Reserved.
18/05/05 22:04:48 See [http://www.uk.research.att.com/vnc](http://www.uk.research.att.com/vnc) for information on VNC
18/05/05 22:04:48 See [http://www.tightvnc.com](http://www.tightvnc.com) for TightVNC-specific information
18/05/05 22:04:48 Desktop name 'X' (triangle:1)
18/05/05 22:04:48 Protocol version supported 3.3
18/05/05 22:04:48 Listening for VNC connections on TCP port 5901
18/05/05 22:04:48 Listening for HTTP connections on TCP port 5801
18/05/05 22:04:48   URL [http://triangle:5801](http://triangle:5801)
Font directory '/usr/X11R6/lib/X11/fonts/Speedo/' not found - ignoring
xrdb: No such file or directory
xrdb: can't open file '/home/brian/.Xresources'
/usr/bin/startxfce4: X server already running on display :1
Option --login is no longer supported in this version of gnome-terminal; you might want to create a profile with the desired setting, and use the new --window-with-profile option
Agent pid 9418
xfce4-session: Another session manager is already running
Agent pid 9418 killed
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".

My /usr/bin/startxfce4
> #!/bin/sh
#
#  xfce4
#
if test x"$XDG_CONFIG_HOME" = x""
then
  BASEDIR=$HOME/.config/xfce4/
else
  BASEDIR=$XDG_CONFIG_HOME/xfce4
fi

if test x"$DISPLAY" = x""
then
  echo "$0: Starting X server"
  prog=xinit
else
  echo "$0: X server already running on display $DISPLAY"
  prog=/bin/sh
fi

if [ -f $BASEDIR/xinitrc ]; then
  exec $prog $BASEDIR/xinitrc $*
elif [ -f $HOME/.xfce4/xinitrc ]; then
  mkdir -p $BASEDIR
  cp $HOME/.xfce4/xinitrc $BASEDIR/
  exec $prog $BASEDIR/xinitrc $*
else
  exec $prog /etc/xdg/xfce4/xinitrc $*
fi  

Any suggestions?

---

### Post by frühstück on 2005-05-19
[QUOTE=sciurus]Xlib: extension "GLX" missing on display ":1.0".[/QUOTE]
i dont think VNC likes opengl [-X

---

### Post by richardwartenburger on 2005-05-19
Is there no alternative remote client software at all that supports openGL 
(vncserver is on ubuntu, client is on Windows)?

---

### Post by sciurus on 2005-05-21
[QUOTE=frühstück]i dont think VNC likes opengl [-X[/QUOTE]

Right, but I think the problem lies in > Agent pid 9418
xfce4-session: Another session manager is already running
Agent pid 9418 killed

---

### Post by Patrick Bolan on 2005-06-08
All the VNC packages I know of do not support OpenGL, but you can replace them with an add-ing that does: [http://xf4vnc.sourceforge.net](http://xf4vnc.sourceforge.net). It replaces the Xvnc executable with a glx-aware version. Works great, the client (vncviewer) has no idea since it's essentially getting screen captures. Uses the graphics card on the server. Recommended.

---

### Post by ubuntu_fire on 2005-06-08
"i dont think VNC likes opengl"

Hey I might have this same problem.  I have a vncserver runnning and a client on WinXP and all I get is a gray screen.   Is this the same problem?

---

