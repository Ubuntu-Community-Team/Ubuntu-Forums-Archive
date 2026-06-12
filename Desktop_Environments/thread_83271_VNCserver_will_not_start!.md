---
title: "VNCserver will not start!"
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

---

### Post by Remmelas on 2005-10-28
sudo nano -w /etc/vnc.conf  (or whatever your favorite editor is)
and add these lines, probably should be filed as a bug.

$fontPath        "unix/:7100"                    # local font server
        # if the local font server has problems, we can fall back on these
        $fontPath .= "/usr/share/X11/fonts/misc,";
        $fontPath .= "/usr/share/X11/fonts/cyrillic,";
        $fontPath .= "/usr/share/X11/fonts/100dpi/:unscaled,";
        $fontPath .= "/usr/share/X11/fonts/75dpi/:unscaled,";
        $fontPath .= "/usr/share/X11/fonts/Type1,";
        $fontPath .= "/usr/share/X11/fonts/CID,";
        $fontPath .= "/usr/share/X11/fonts/100dpi,";
        $fontPath .= "/usr/share/X11/fonts/75dpi,";
        # paths to defoma fonts
        $fontPath .= "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,";
        $fontPath .= "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID";

---

