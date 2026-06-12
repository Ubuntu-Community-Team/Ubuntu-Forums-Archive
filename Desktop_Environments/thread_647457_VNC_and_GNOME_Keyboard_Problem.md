---
title: "VNC and GNOME Keyboard Problem"
date: 2007-12-22
forum: Desktop Environments
---

### Post by Belistner20007 on 2007-12-22
Hi,
I'm having problems with VNC and keyboard layouts. I've looked everywhere for the answer to this with no avail - any help is greatly appreciated.

For the sake of simplicity I have created a separate profile for logging in via VNC.  When I log in at the local machine everything is fine and the keyboard is mapped correctly.

When I log in via VNC I cannot select a keyboard layout that works. If I go to System -> Preferences -> Keyboard under layouts there aren't the same options as when you log in locally. The only model available is "Generic Keyboard" and none of the layouts for UK work at all.

I figure GNOME isnt getting told to load the layouts like it would locally - but I don't know much about this. I guess I'm missing a command when starting the session. My xstart file for the VNC session is below:

```

##!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
gnome-session &
```

I am using tightvnc

Unfortunately I've reached the edge of my current Linux knowledge!! I don't know where Gnome gets its keyboard settings and stuff like that. I tried to find what commands the GDM executes when it starts a session, but it appears to be just "gnome-session" like I have above.

Thanks for ANY help
Lewis

---

