---
title: "Resolution problem when connecting to Ubuntu via vnc"
date: 2013-10-21
forum: Desktop Environments
---

### Post by erez2 on 2013-10-21
I'm using the following xstartup file, but when I connect (from a Windows laptop), I don't see the Unity desktop in fullscreen mode:

```
#!/bin/sh

# VNC Server (Virtual-Mode) start-up script compatible with Ubuntu 12.04

[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey

vncconfig -iconic &

if [ -f /usr/bin/gnome-session ]; then
  # Some gnome session types won't work with Xvnc, try to pick a sensible
  # default.
  for SESSION in "ubuntu-2d" "2d-gnome"; do
    if [ -f /usr/share/gnome-session/sessions/$SESSION.session ]; then
      DESKTOP_SESSION=$SESSION; export DESKTOP_SESSION
      GDMSESSION=$SESSION; export GDMSESSION
      STARTUP="/usr/bin/gnome-session --session=$SESSION"; export STARTUP
    fi
  done
fi

if   [ -x /etc/X11/Xsession ]; then /etc/X11/Xsession
elif [ -x /etc/X11/xdm/Xsession ]; then /etc/X11/xdm/Xsession
elif [ -x /etc/X11/xinit/Xsession ]; then /etc/X11/xinit/Xsession
elif [ -x /etc/gdm/Xsession ]; then /etc/gdm/Xsession gnome-session
elif [ -x /etc/kde/kdm/Xsession ]; then /etc/kde/kdm/Xsession
elif [ -x /usr/dt/bin/Xsession ]; then
  XSTATION=1 DTXSERVERLOCATION=local /usr/dt/bin/Xsession
elif [ -x /usr/dt/bin/dtsession ]; then /usr/dt/bin/dtsession
else
  if which twm > /dev/null 2>&1; then
    #xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
    xterm -geometry 1280x1024 -ls -title "$VNCDESKTOP Desktop" &
    twm
  else
    #xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop"
    xterm -geometry 1280x1024 -ls -title "$VNCDESKTOP Desktop"
  fi
fi

vncserver -kill $DISPLAY
```

---

