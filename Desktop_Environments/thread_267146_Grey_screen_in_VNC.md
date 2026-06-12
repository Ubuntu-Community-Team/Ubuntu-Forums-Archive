---
title: "Grey screen in VNC"
date: 2006-09-28
forum: Desktop Environments
---

### Post by zurih on 2006-09-28
Hi

I'm trying to configure and use vncserver correctly.
I installed tightvncsevrer & x11vnc packages.

When I start the tightvncserver and trying to connect to the desktop, I'm getting a grey screen with X cursor.

This is the log from the session:

```

Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'
MAXSOCKS=1000
28/09/06 15:22:52 Xvnc version 3.3.tight1.2.9
28/09/06 15:22:52 Copyright (C) 1999 AT&T Laboratories Cambridge.
28/09/06 15:22:52 Copyright (C) 2000-2002 Constantin Kaplinsky.
28/09/06 15:22:52 All Rights Reserved.
28/09/06 15:22:52 See http://www.uk.research.att.com/vnc for information on VNC
28/09/06 15:22:52 See http://www.tightvnc.com for TightVNC-specific information
28/09/06 15:22:52 Desktop name 'X' (zurih-desktop:1)
28/09/06 15:22:52 Protocol version supported 3.3
28/09/06 15:22:52 Listening for VNC connections on TCP port 5901
Font directory '/usr/share/X11/fonts/Speedo/' not found - ignoring
Xvnc: dispatch: MaxClients = 1000
/home/zurih/.vnc/xstartup: line 5: /etc/X11/xinit/xinitrc: Permission denied
/home/zurih/.vnc/xstartup: line 5: exec: /etc/X11/xinit/xinitrc: cannot execute: Success

28/09/06 15:22:56 Got connection from client 192.117.236.29
28/09/06 15:22:56 Protocol version 3.5
28/09/06 15:22:56 Ignoring minor version mismatch
28/09/06 15:22:58 Full-control authentication passed by 192.117.236.29
28/09/06 15:22:58 Pixel format for client 192.117.236.29:
28/09/06 15:22:58   32 bpp, depth 24, little endian
28/09/06 15:22:58   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
28/09/06 15:22:58   no translation needed
28/09/06 15:22:58 Using tight encoding for client 192.117.236.29
28/09/06 15:22:58 rfbProcessClientNormalMessage: ignoring unknown encoding 8
28/09/06 15:22:58 Enabling X-style cursor updates for client 192.117.236.29
28/09/06 15:22:58 Enabling cursor position updates for client 192.117.236.29
28/09/06 15:22:58 Using image quality level 6 for client 192.117.236.29
28/09/06 15:22:58 Enabling LastRect protocol extension for client 192.117.236.29
28/09/06 15:22:58 rfbProcessClientNormalMessage: ignoring unknown encoding -223
28/09/06 15:23:02 Client 192.117.236.29 gone
28/09/06 15:23:02 Statistics:
28/09/06 15:23:02   key events received 0, pointer events 21
28/09/06 15:23:02   framebuffer updates 1, rectangles 15, bytes 1068
28/09/06 15:23:02     LastRect markers 1, bytes 12
28/09/06 15:23:02     cursor shape updates 1, bytes 82
28/09/06 15:23:02     cursor position updates 1, bytes 12
28/09/06 15:23:02     tight rectangles 12, bytes 962
28/09/06 15:23:02   raw bytes equivalent 3145740, compression ratio 3270.000000

```

Can anyone point out what is the problem?

Thanks in advance.

---

### Post by bswilson on 2006-09-28
When I see this, I think that maybe you need to use **sudo**:

```
/home/zurih/.vnc/xstartup: line 5: /etc/X11/xinit/xinitrc: Permission denied
/home/zurih/.vnc/xstartup: line 5: exec: /etc/X11/xinit/xinitrc: cannot execute: Success
```

Are you launching **vncserver** with **sudo**?

---

### Post by zurih on 2006-09-28
> **bswilson said:**
> When I see this, I think that maybe you need to use **sudo**:

```
/home/zurih/.vnc/xstartup: line 5: /etc/X11/xinit/xinitrc: Permission denied
/home/zurih/.vnc/xstartup: line 5: exec: /etc/X11/xinit/xinitrc: cannot execute: Success
```

Are you launching **vncserver** with **sudo**?

well, when I try running sudo I get:
```
sudo vncserver 
vncserver: Wrong type or access mode of /home/username/.vnc.
```

---

### Post by charles.g.moore on 2006-09-28
I dont know if this helps but when I installed vnc4Server it seemed like I configured everything correctly but I also got a grey screen.
Someone told me to reboot (Iknow you shouldnt have to with Linux) and it worked!!!
Try it who knows...

---

### Post by zurih on 2006-09-28
> **charles.g.moore said:**
> I dont know if this helps but when I installed vnc4Server it seemed like I configured everything correctly but I also got a grey screen.
Someone told me to reboot (Iknow you shouldnt have to with Linux) and it worked!!!
Try it who knows...

Already rebooted, nothing changed.

What about:
Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'
and
Font directory '/usr/share/X11/fonts/Speedo/' not found - ignoring
?

---

### Post by zurih on 2006-09-29
> **zurih said:**
> Already rebooted, nothing changed.

What about:
Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'
and
Font directory '/usr/share/X11/fonts/Speedo/' not found - ignoring
?

no one?

---

### Post by rick_1010 on 2006-10-10
I'm having the same problem with Xubuntu and VNC, I've tried all the different remote access programs in the repositories (including Dapper Drake universe) and I have this problem for all of them (or I just get a white screen, but this is just for the ones meant for KDE so I'm assuming that is the reason). 

I think there is a possibility that the XFCE4 desktop does not support VNC properly. I hope it does though and that I can resolve this, I will post if I can figure it out.

---

### Post by rick_1010 on 2006-10-10
Are you using Ubuntu or Xubuntu?

---

### Post by talz13 on 2006-10-22
I'm also having this problem on a fresh install of Ubuntu.  I just reinstalled over my old 5.10 install, and left my home partition intact.  In my vncserver log file I get:```
Xvnc Free Edition 4.1.1
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.
Underlying X server release 70000000, The X.Org Foundation


Sun Oct 22 02:53:21 2006
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      created VNC server for screen 0
error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/share/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/share/X11/fonts/OTF, removing from list!
Could not init font path element /usr/share/X11/fonts/CID/, removing from list!
sh: /home/jeff/.vnc/xstartup: Permission denied
```

---

### Post by xpavement on 2006-10-31
*EDIT* Found the answer to my issue, added this to the top of the xstartup, found in one of the links above: 

unset SESSION_MANAGER

I restarted my tightvnc server and now I get the xfce4 desktop loaded.

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
I had xfce4 working on my vnc connection before the upgrade to Edgy, now it's giving me the "session manager already running" message when it attempts to execute xfce4-session in my .vnc/xstartup file, so I get the grey screen instead. I changed the xstartup file to start a terminal session, so at least I can use that remotley, but I would like the whole desktop back the way it was. No one seems to have an answer as to how to bypass this particular message.

---

### Post by pkbarber on 2006-12-11
> **zurih said:**
> no one?

I had an issue dealing with my fonts as well... I realize your post is old but I just saw it.  

[http://ubuntuforums.org/showthread.php?t=122402&page=19&highlight=vnc+6.10](http://ubuntuforums.org/showthread.php?t=122402&page=19&highlight=vnc+6.10)

#186

---

### Post by mondo1287 on 2008-04-16
Sorry for dragging out an old post, but for those with this problem the issue is permissions on ~/.vnc/xstartup.   You need to do chmod +x ~/.vnc/xstartup.

---

