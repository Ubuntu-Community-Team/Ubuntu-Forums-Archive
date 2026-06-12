---
title: "VNC could not acquire name on session bus"
date: 2010-08-23
forum: Desktop Environments
---

### Post by PuckstopperGA on 2010-08-23
Hi all,

I'm experiencing a problem when trying to use VNC on my desktop box. Whenever I try to connect, I get a gray screen with the error "could not acquire name on session bus". 

I've searched the forums, but after trying several solutions, nothing has seemed to work for me.

My xstartup file looks like this:

```
#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
# Fix to make GNOME work
export XKL_XMODMAP_DISABLE=1
/etc/X11/Xsession

```

Any assistance would be greatly appreciated!

---

### Post by PuckstopperGA on 2010-08-23
Little extra info, my session logfile:

```
23/08/10 11:25:05 Xvnc version TightVNC-1.3.9
23/08/10 11:25:05 Copyright (C) 2000-2007 TightVNC Group
23/08/10 11:25:05 Copyright (C) 1999 AT&T Laboratories Cambridge
23/08/10 11:25:05 All Rights Reserved.
23/08/10 11:25:05 See http://www.tightvnc.com/ for information on TightVNC
23/08/10 11:25:05 Desktop name 'X' (<redacted>:1)
23/08/10 11:25:05 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
23/08/10 11:25:05 Listening for VNC connections on TCP port 5901
xrdb: No such file or directory
xrdb: can't open file '/home/<redacted>/.Xresources'

23/08/10 11:25:12 Got connection from client 127.0.0.1
23/08/10 11:25:12 Using protocol version 3.8
23/08/10 11:25:12 Full-control authentication passed by 127.0.0.1
23/08/10 11:25:12 Pixel format for client 127.0.0.1:
23/08/10 11:25:12   32 bpp, depth 24, little endian
23/08/10 11:25:12   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
23/08/10 11:25:12   no translation needed
23/08/10 11:25:12 rfbProcessClientNormalMessage: ignoring unknown encoding 16
23/08/10 11:25:12 Using tight encoding for client 127.0.0.1
23/08/10 11:25:12 rfbProcessClientNormalMessage: ignoring unknown encoding 8
```

Tunneling over SSH, but same problems when I try inside the network.

---

### Post by PuckstopperGA on 2010-08-25
Ok well I found a workaround for this. After lots of googling, I found that compiz doesn't play well with many VNC servers. x11vnc seems to be the only one that will work.

For anyone who googles their way here:

```
x11vnc --xkb --noxdamage --passwd XXXXX -forever -shared -alwaysshared
```

Sure makes me miss MS RDP!!

---

### Post by karagorge on 2011-12-16
> **PuckstopperGA said:**
> Ok well I found a workaround for this. After lots of googling, I found that compiz doesn't play well with many VNC servers. x11vnc seems to be the only one that will work.

For anyone who googles their way here:

```
x11vnc --xkb --noxdamage --passwd XXXXX -forever -shared -alwaysshared
```

Sure makes me miss MS RDP!!

This works - I tried several other methods but this [for now] is the only one that worked. The only thing now you have to make sure are the ports. They have to be opened.

(if you are using router -> open router 192.168.1.1 -> Applications & Gaming:

Application [CUSTOM_NAME] - Start [vnc uses 5900 and above so this field = 5900]

End [As many ports as you wish, example = 10]

Protocol [Both] 

IP address [Your private ip address - type 'ifconfig' in terminal to find it out] 

Enable [Check it] and click the save button bellow.)

Hope this helps ---

Thanks again

---

