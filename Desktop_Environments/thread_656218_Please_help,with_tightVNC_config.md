---
title: "Please help,with tightVNC config"
date: 2008-01-02
forum: Desktop Environments
---

### Post by malibu on 2008-01-02
Hi there.. I'm in the process of making the switch from Windows to Ubuntu on my main home PC.  I'm currently having a problem with the remote desktops.  I've long wished for my wife and I to both be able to have simultaneous desktops on the system.  I read that tightvnc server could do this so I installed it.  I can connect (via the :1 method) just fine.. I have windows and a menu bar and all that.. It's unfortunate that there is no desktop graphic, but no show-stopper by any means.  Here are my two problems:

1) There are no icons on the actual desktop and I cannot interact with it in any way.  Ie. If I download with firefox and save something on the desktop it goes into a back hole.  Likewise if I drag something onto the desktop.

2) It's not good enough to identify the first desktop as <my machine>:1 and the second desktop as <my machine>:2.  Isn't there a way for my wife to provide her ID and get her desktop and likewise for myself?

Currently i'm installing tightvncserver manually by signing in and executing 'vncserver'.  My xstartup script looks like this:

```

#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid navy
x-window-manager &
gnome-panel 2> /dev/null &
xterm &

```

Any help would be appreciated, thanks!

---

### Post by Zafrusteria on 2008-01-02
The xstartup script I use is this

```
#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
gnome-session &
```

You should get a gnome session by just changing your script from gnome-panel to gnome-session. Remember to put it into the backbround with a "&" :-)

---

### Post by malibu on 2008-01-02
It works awesome!  Thanks so much.  But one problem.. My keyboard mapping gets all messed up with gnome-session.  I kill the VNC server process and restart with gnome-panel and it's fine again.

Know what could be causing it?

---

### Post by malibu on 2008-01-02
In case anyone also ends up with this problem, modifying my xstart seems to have solved it.  Works nicely now (this was Ubuntu gutsy BTW):

```

#!/bin/sh

xrdb $HOME/.Xresources
gnome-wm &
gnome-panel &
nautilus --no-default-window &
gnome-cups-icon &
gnome-volume-manager &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &

```

---

