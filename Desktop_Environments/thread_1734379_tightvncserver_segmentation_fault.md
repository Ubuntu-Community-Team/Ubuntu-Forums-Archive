---
title: "tightvncserver segmentation fault"
date: 2011-04-20
forum: Desktop Environments
---

### Post by m_gustafsson on 2011-04-20
Hi,

I have a desktop with Ubuntu 10.10 running tightvncserver 1.3.9-6.1 to which I connect from a laptop with Ubuntu 10.10 using xvnc4viewer 4.1.1+xorg4.3.0-37ubuntu.

Quite often programs crashes, e.g Thunderbird does while I try to attach documents and Nautilius if I press arrow down. If I start them from a terminal I get the following (when they crash):

```
$ thunderbird
Xlib:  extension "RANDR" missing on display ":1.0".
Segmentation fault

$ nautilus
Xlib:  extension "RANDR" missing on display ":1.0".
```

I have tried to use xvncviewer as an alternate viewer and vnc4server as well as tightvncserver 1.3.10 as servers, but I get very similar crashes.

The log looks like this:
```
$ cat .vnc/desktop3\:1.log
20/04/11 07:34:16 Xvnc version TightVNC-1.3.9
20/04/11 07:34:16 Copyright (C) 2000-2007 TightVNC Group
20/04/11 07:34:16 Copyright (C) 1999 AT&T Laboratories Cambridge
20/04/11 07:34:16 All Rights Reserved.
20/04/11 07:34:16 See http://www.tightvnc.com/ for information on TightVNC
20/04/11 07:34:16 Desktop name 'X' (desktop3:1)
20/04/11 07:34:16 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
20/04/11 07:34:16 Listening for VNC connections on TCP port 5901

20/04/11 07:34:24 Got connection from client 192.168.0.133
20/04/11 07:34:24 Using protocol version 3.8
20/04/11 07:34:26 Full-control authentication passed by 192.168.0.133
20/04/11 07:34:26 Pixel format for client 192.168.0.133:
20/04/11 07:34:26   8 bpp, depth 6
20/04/11 07:34:26   true colour: max r 3 g 3 b 3, shift r 4 g 2 b 0
20/04/11 07:34:26 Enabling full-color cursor updates for client 192.168.0.133
20/04/11 07:34:26 rfbProcessClientNormalMessage: ignoring unknown encoding -223
20/04/11 07:34:26 rfbProcessClientNormalMessage: ignoring unknown encoding 16
20/04/11 07:34:26 Using hextile encoding for client 192.168.0.133
20/04/11 07:34:27 Pixel format for client 192.168.0.133:
20/04/11 07:34:27   32 bpp, depth 24, little endian
20/04/11 07:34:27   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
20/04/11 07:34:27   no translation needed
20/04/11 07:34:27 Enabling full-color cursor updates for client 192.168.0.133
20/04/11 07:34:27 rfbProcessClientNormalMessage: ignoring unknown encoding -223
20/04/11 07:34:27 Using hextile encoding for client 192.168.0.133
20/04/11 07:34:27 rfbProcessClientNormalMessage: ignoring unknown encoding 16
20/04/11 07:54:43 KbdAddEvent: unknown KeySym 0xffb7 - allocating KeyCode 89
20/04/11 07:54:43 KbdAddEvent: unknown KeySym 0xffb1 - allocating KeyCode 90
```

If anyone has any suggestion about what my problem might be, or how to trouble shoot this it would be very much appreciated.

/Mats

---

### Post by m_gustafsson on 2011-04-26
I can also add that the server is a 64-bit capable computer, but I believe that I have installed the 32-bit Ubuntu on it.
```
$ uname -a
Linux desktop3 2.6.35-28-generic-pae #50-Ubuntu SMP Fri Mar 18 20:43:15 UTC 2011 i686 GNU/Linux
```

I just tried to set up another computer (a 32-bit processor, with Ubuntu 10.10) with tightvncserver, and when running xvnc4viewer towards it I don't experience the same problems.

---

### Post by m_gustafsson on 2011-05-19
Switching to 11.04 on both my desktop and my laptop seems to have solved most of the problems that I saw in 10.10.

---

