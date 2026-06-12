---
title: "Ubuntu Server 14.04 VNC Viewer shows a blank screen"
date: 2016-07-07
forum: Desktop Environments
---

### Post by raphytaffy on 2016-07-07
I have installed **vncserver** through this guide: [https://www.howtoforge.com/tutorial/ubuntu-gnome-vnc-headless-server/](https://www.howtoforge.com/tutorial/ubuntu-gnome-vnc-headless-server/)

I want to use **icewm**, so I installed it with:
```
apt-get install icewm icewm-themes
```

I have also tried to install these packages:
```
apt-get install xvfb
sudo apt-get install x11-xkb-utils xfonts-100dpi xfonts-75dpi xfonts-scalable xfonts-cyrillic x11-apps
```

I must still be missing something because when I connect through VNC Viewer, all I see is this:
[http://i.imgur.com/5PkkX6o.jpg](http://i.imgur.com/5PkkX6o.jpg)

My **xstartup** looks like:
```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
exec /etc/X11/xinit/xinitrc


[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid black
vncconfig -iconic &
icewm-session &
```

My log file shows this when a client is connected:
```
Xvnc Free Edition 4.1.1 - built Jul 31 2015 19:10:31
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.
Underlying X server release 40300000, The XFree86 Project, Inc




Wed Jul  6 22:15:40 2016
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      created VNC server for screen 0
error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Speedo/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/misc/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/75dpi/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/100dpi/, removing from list!
/home/raphytaffy/.vnc/xstartup: 5: exec: /etc/X11/xinit/xinitrc: Permission denied


Wed Jul  6 22:15:59 2016
 Connections: accepted: 0.0.0.0::52410
 SConnection: Client needs protocol version 3.8
 SConnection: Client requests security type VncAuth(2)


Wed Jul  6 22:16:02 2016
 VNCSConnST:  Server default pixel format depth 16 (16bpp) little-endian rgb565
 VNCSConnST:  Client pixel format depth 8 (8bpp) colour-map
 VNCSConnST:  Client pixel format depth 16 (16bpp) little-endian rgb565


Wed Jul  6 22:16:06 2016
 Connections: closed: 0.0.0.0::52410 (Clean disconnection)
 SMsgWriter:  framebuffer updates 3
 SMsgWriter:    raw rects 1, bytes 17612
 SMsgWriter:    hextile rects 1, bytes 1451414
 SMsgWriter:    ZRLE rects 2, bytes 1310
 SMsgWriter:    raw bytes equivalent 4337904, compression ratio 2.950281
```

I can provide any other information necessary, but I'm a bit stuck here.

---

### Post by wildmanne39 on 2016-07-08
Please use thumbnails or Url's when posting images because many people have slow internet connections and loading pages with large images is very difficult for them.

---

### Post by steeldriver on 2016-07-08
```

/home/raphytaffy/.vnc/xstartup: 5: exec: /etc/X11/xinit/xinitrc: Permission denied

```

fails, and because you're exec'ing it (i.e. passing control to it) the session fails before getting to your custom session (icewm-session)

---

### Post by raphytaffy on 2016-07-10
> **Wild Man said:**
> Please use thumbnails or Url's when posting images because many people have slow internet connections and loading pages with large images is very difficult for them.

Apologies, will do that in the future.

> **steeldriver said:**
> ```

/home/raphytaffy/.vnc/xstartup: 5: exec: /etc/X11/xinit/xinitrc: Permission denied

```

fails, and because you're exec'ing it (i.e. passing control to it) the session fails before getting to your custom session (icewm-session)

Good catch! I changed the permissions of **/etc/X11/xinit/xinitrc** to **755**. The error no longer shows in the log, but a few other errors still persist:
```
Xvnc Free Edition 4.1.1 - built Jul 31 2015 19:10:31Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.
Underlying X server release 40300000, The XFree86 Project, Inc




Sun Jul 10 12:40:03 2016
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      created VNC server for screen 0
error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Speedo/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/misc/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/75dpi/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/100dpi/, removing from list!


Sun Jul 10 12:40:19 2016
 Connections: accepted: 0.0.0.0::50459
 SConnection: Client needs protocol version 3.8
 SConnection: Client requests security type VncAuth(2)


Sun Jul 10 12:40:21 2016
 VNCSConnST:  Server default pixel format depth 16 (16bpp) little-endian rgb565
 VNCSConnST:  Client pixel format depth 8 (8bpp) colour-map
 VNCSConnST:  Client pixel format depth 16 (16bpp) little-endian rgb565


Sun Jul 10 12:40:27 2016
 Connections: closed: 0.0.0.0::50459 (Clean disconnection)
 SMsgWriter:  framebuffer updates 4
 SMsgWriter:    raw rects 1, bytes 17612
 SMsgWriter:    hextile rects 3, bytes 1451910
 SMsgWriter:    ZRLE rects 2, bytes 1310
 SMsgWriter:    raw bytes equivalent 4338952, compression ratio 2.949998
```

Contents of **.vnc/xstartup**:
```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
exec /etc/X11/xinit/xinitrc


[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
icewm-session &
```

I'm able to log into the VNC session, but the grey screen is all I see.

---

### Post by steeldriver on 2016-07-10
I'm not sure why you're trying to exec that anyway

AFAIK all it does is invoke /etc/X11/Xsession which basically searches a bunch of places for your session of choice. And it never returns (exec **replaces** the current process - i.e. the xstartup script - with the named command) so the remaining lines (where you spawn the icewm-session) are ignored

When using VNC, your xstartup file should already contain the session information

Does it work if you simply comment out the line

```

# exec /etc/X11/xinit/xinitrc

```

---

### Post by raphytaffy on 2016-07-10
> **steeldriver said:**
> Does it work if you simply comment out the line

```

# exec /etc/X11/xinit/xinitrc

```

Oh man, I'm dense today. Didn't realize what your previous post was pointing out. Working great now :)

---

### Post by steeldriver on 2016-07-10
Well I honestly never understood /etc/X11/Xsession so I hope there's nothing in it that is essential! I think it basically just reads custom resources (which you probably don't have anyway - and should be covered by the xrdb command)

---

