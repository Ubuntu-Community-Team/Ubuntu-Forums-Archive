---
title: "Running Xvnc4 via SSH-connection gives me a checkered screen when connecting"
date: 2008-05-17
forum: Desktop Environments
---

### Post by runesvend on 2008-05-17
Hello all!

UPDATE: I think the problem is that the window manager, XFCE, has, for some reason stopped. So the only means I have to connect to the PC is by SSH. I've tried running several commands, like startxfce4, but they all amount to this:

```
Derre@ks354621:/etc/xdg/xfce4$ startxfce4
/usr/bin/startxfce4: X server already running on display ks354621.kimsufi.com:1
xrdb: Connection refused
xrdb: Can't open display 'ks354621.kimsufi.com:1'
/etc/xdg/xfce4/xinitrc: line 58: xscreensaver: command not found
Agent pid 2541

(xfce4-session:2549): Gtk-WARNING **: cannot open display:  
Agent pid 2541 killed

```

This happens with every graphical application I try to run. DISPLAYNAME contains "ks354621.kimsufi.com:1" while HOSTNAME contains "ks354621.kimsufi.com". I've added an entry from my local Xauthority-file, so *xauth list* gives the following output:

```
ks354621:/etc/xdg/xfce4# xauth list
rune/unix:0  MIT-MAGIC-COOKIE-1  7b361001ba1cd2a9da5d276be09abff1
ks354621.kimsufi.com:1  MIT-MAGIC-COOKIE-1  75e1930981208a9daedab68df5d7ea11
```

**How do I, via SSH, start a window manager on this remote machine's own display so I can start using VNC again?**

All input is appreciated!

Old part (still relevant):

I'm in a bit of trouble. For a friend I wanted to try to change the resolution of the VNC session that Xvnc4 gives him.

In the start, connected via SSH to the remote machine for which I wished to change the resolution of sessions created by the Xvnc4 service, I used *ps -ax* to find the arguments which were used for Xvnc4 that was already running (and working) and they were the following (according to *ps*):

```
Xvnc4 :1 -desktop <removed> -auth /home/Derre/.Xauthority -geometry 1024x768 -depth 24 -rfbwait 30000 -rfbauth /home/Derre/.vnc/passwd -rfbport 5901 -pn -fp /usr/X11R6/lib/X11/fonts/Type1/,/usr/X11R6/lib/X11/fonts/Speedo/,/usr/X11R6/lib/X11/fonts/misc/,/usr/X11R6/lib/X11/fonts/75dpi/,/usr/X11R6/lib/X11/fonts/100dpi/,/usr/share/fonts/X11/misc/,/usr/share/fonts/X11/Type1/,/usr/share/fonts/X11/75dpi/,/usr/share/fonts/X11/100dpi/ -co /etc/X11/rgb
```

I could see this was running in the background. I killed it with *kill <pid>* and then ran the above command from a SSH-connection to the host. When this is done, this is the output:

```
Derre@ks354621:~/Desktop$ Xvnc4 :1 -desktop <removed> -auth /home/Derre/.Xauthority -geometry 1024x768 -depth 24 -rfbwait 30000 -rfbauth /home/Derre/.vnc/passwd -rfbport 5901 -pn -fp /usr/X11R6/lib/X11/fonts/Type1/,/usr/X11R6/lib/X11/fonts/Speedo/,/usr/X11R6/lib/X11/fonts/misc/,/usr/X11R6/lib/X11/fonts/75dpi/,/usr/X11R6/lib/X11/fonts/100dpi/,/usr/share/fonts/X11/misc/,/usr/share/fonts/X11/Type1/,/usr/share/fonts/X11/75dpi/,/usr/share/fonts/X11/100dpi/ -co /etc/X11/rgb

Xvnc Free Edition 4.1.1 - built Feb 26 2007 20:43:44
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
Underlying X server release 40300000, The XFree86 Project, Inc


Sat May 17 10:38:04 2008
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      created VNC server for screen 0
error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Speedo/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/misc/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/75dpi/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/100dpi/, removing from list!
Could not init font path element /usr/share/fonts/X11/Type1/, removing from list!
Could not init font path element /usr/share/fonts/X11/75dpi/, removing from list!
Could not init font path element /usr/share/fonts/X11/100dpi/, removing from list!

```

When I try to connect to the server using *xvnc4viewer <ip>:1* I am greeted with a screen looking like the attached picture with an "X" as a cursor.

As far as I can see the process that was running was the same before and after the change.

I've tried running the above commands locally on my machine and there they work fine.

HELP! :( Does anyone know what to do?

---

