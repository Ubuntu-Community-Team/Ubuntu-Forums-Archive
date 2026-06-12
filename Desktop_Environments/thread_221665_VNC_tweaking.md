---
title: "VNC tweaking"
date: 2006-07-23
forum: Desktop Environments
---

### Post by PokerFacePenguin on 2006-07-23
I have installed a server (Xubuntu desktop) and have got it to run vncserver.   When I connect to this server using vncviewer hostname:screennumber I get only a terminal window inside of an X window environment.  My problem is "How do I get to view the desktop, wallpaper, etc (in an XFce environment - Xubuntu)?  Is my ~/.vnc/xstartup file missing something?  Here is what is looks like:

```

#!/bin/sh
xrdb $HOME/.Xresources
xsetroot -solid grey
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &
Xsession &

```

which produces the following view from a remote machine using vncviewer:

[http://flickr.com/photo_zoom.gne?id=196623822&size=o]("http://flickr.com/photo_zoom.gne?id=196623822&size=o")

I have no Panel at the bottom or anything ...:confused: 
](*,)

---

### Post by PokerFacePenguin on 2006-07-24
A local vncviewer session produces the same result as a remote one, so think I can safely say this is about how my x displays in the viewer.  

Any constructive/insightful comments appreciated...

---

### Post by hfdragon on 2006-09-04
Just did the same thing and my solution is to modify the ~/.vnc/xstartup file like this :
```

#!/bin/sh
startxfce4 &
```

:-)

---

