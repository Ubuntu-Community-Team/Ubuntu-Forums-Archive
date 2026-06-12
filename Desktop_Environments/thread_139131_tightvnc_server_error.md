---
title: "tightvnc server error"
date: 2006-03-03
forum: Desktop Environments
---

### Post by mxc on 2006-03-03
Hi all,

I set up a machine with the server option. I now need to login and run a browser over it. (its a long story but I have to do this with the current resources). I did an apt-get install tightvncserver.

When I go vncviewer :1, after entering the passwords I get 

Font directory '/usr/share/X11/fonts/cyrillic' not found - ignoring
Font directory '/usr/share/X11/fonts/100dpi/:unscaled' not found - ignoring
Font directory '/usr/share/X11/fonts/Type1' not found - ignoring
Font directory '/usr/share/X11/fonts/CID' not found - ignoring
Font directory '/usr/share/X11/fonts/100dpi' not found - ignoring
Font directory '/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType' not found - ignoring
Font directory '/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID' not found - ignoring

Fatal server error:
could not open default font 'fixed'
03/03/06 17:28:33 Xvnc version 3.3.tight1.2.9
03/03/06 17:28:33 Copyright (C) 1999 AT&T Laboratories Cambridge.
03/03/06 17:28:33 Copyright (C) 2000-2002 Constantin Kaplinsky.
03/03/06 17:28:33 All Rights Reserved.
03/03/06 17:28:33 See [http://www.uk.research.att.com/vnc](http://www.uk.research.att.com/vnc) for information on VNC
03/03/06 17:28:33 See [http://www.tightvnc.com](http://www.tightvnc.com) for TightVNC-specific information
03/03/06 17:28:33 Desktop name 'X' (cubitlast:1)
03/03/06 17:28:33 Protocol version supported 3.3
03/03/06 17:28:33 Listening for VNC connections on TCP port 5901
Font directory '/usr/X11R6/lib/X11/fonts/misc/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/Speedo/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/Type1/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/75dpi/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/100dpi/' not found - ignoring

Fatal server error:
could not open default font 'fixed'


How do I fix this. The /etc/vnc.conf file doesnt have much in it. I added the following to the vnc.conf file as per the ebuntu wiki.

$fontPath "unix/:7100" # local font server
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


I did not have any x stuff installed before installing tightvnc.

thanks

---

### Post by Swiss on 2006-03-03
Goto: System>Administration>Synaptic Package Manager.

Make sure you have the "Universe" dir enabled, then search for:

```
xvnc4viewer
```


See if that works...

I may also be that you don't have the correct font installed to view the said remote computer.

---

### Post by mxc on 2006-03-03
ok -- i needed to do

apt-get install xfonts-base. I can now vnc into the server. There appears to be no windows manager though. I do I install the min amount for gnome?

---

### Post by Swiss on 2006-03-03
Use xvnc4viewer, it has a window manager... I use xvnc4viewer in my office and it works a charm...

---

