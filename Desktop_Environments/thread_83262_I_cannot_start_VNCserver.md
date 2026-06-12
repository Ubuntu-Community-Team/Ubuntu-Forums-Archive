---
title: "I cannot start VNCserver"
date: 2005-10-28
forum: Desktop Environments
---

### Post by dazzla on 2005-10-28
Hi guys, i'm having real problems getting VNCserver running.

I installed vnc4server using apt, set a password and tried to start it but it won't start giving me the following error:

```
Couldn't start Xtightvnc; trying default font path.
Please set correct fontPath in the vncserver script.
Couldn't start Xtightvnc process.

28/10/05 13:46:16 Xvnc version 3.3.tight1.2.9
28/10/05 13:46:16 Copyright (C) 1999 AT&T Laboratories Cambridge.
28/10/05 13:46:16 Copyright (C) 2000-2002 Constantin Kaplinsky.
28/10/05 13:46:16 All Rights Reserved.
28/10/05 13:46:16 See http://www.uk.research.att.com/vnc for information on VNC
28/10/05 13:46:16 See http://www.tightvnc.com for TightVNC-specific information
28/10/05 13:46:16 Desktop name 'X' (ubuntu:2)
28/10/05 13:46:16 Protocol version supported 3.3
28/10/05 13:46:16 Listening for VNC connections on TCP port 5902
Font directory '/usr/X11R6/lib/X11/fonts/Type1/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/Speedo/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/misc/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/75dpi/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/100dpi/' not found - ignoring

Fatal server error:
could not open default font 'fixed'
28/10/05 13:46:17 Xvnc version 3.3.tight1.2.9
28/10/05 13:46:17 Copyright (C) 1999 AT&T Laboratories Cambridge.
28/10/05 13:46:17 Copyright (C) 2000-2002 Constantin Kaplinsky.
28/10/05 13:46:17 All Rights Reserved.
28/10/05 13:46:17 See http://www.uk.research.att.com/vnc for information on VNC
28/10/05 13:46:17 See http://www.tightvnc.com for TightVNC-specific information
28/10/05 13:46:17 Desktop name 'X' (ubuntu:2)
28/10/05 13:46:17 Protocol version supported 3.3
28/10/05 13:46:17 Listening for VNC connections on TCP port 5902
Font directory '/usr/X11R6/lib/X11/fonts/misc/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/Speedo/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/Type1/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/75dpi/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/100dpi/' not found - ignoring

Fatal server error:
could not open default font 'fixed'

```

This was a fresh build of Breezy, i had no problems getting it working at all on Hoary.  to make matters worse i have now built  laptop and it does the same thing there.  Surely something i am missing out.

Thanks in advance

NUTS: cn a mod please move this to the general Desktop support of Ubuntu please, i'm not using Kubuntu

---

### Post by HermanAB on 2005-10-28
It's been a while since I played with VNC, but maybe you can find something helpful here: [http://www.aerospacesoftware.com/vnc-howto.html](http://www.aerospacesoftware.com/vnc-howto.html)

Cheers,

H

---

### Post by ubuntuede on 2005-10-28
Hi,

check for the path '/usr/X11R6/lib/X11/fonts' if it exists or not ...
if not create a link to the proper font path (xset -q).

cd /usr/X11R6/lib/X11
sudo ln -s "pathtox11fonts" fonts

ede

---

### Post by magikx21 on 2007-10-08
I setup a VNC with TightVNC and I double checked it with that link but I have an issue still. I can connect but when the window opens all it shows is a Konsole window in the upper right hand corner. Anyone else run into this issue.

---

### Post by gnychis on 2007-12-15
solution for me, add this to vnc.conf:
$fontPath .= "/usr/share/fonts/X11/misc/,";

---

