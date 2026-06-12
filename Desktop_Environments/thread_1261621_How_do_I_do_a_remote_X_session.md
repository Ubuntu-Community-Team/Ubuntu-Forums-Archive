---
title: "How do I do a remote X session?"
date: 2009-09-08
forum: Desktop Environments
---

### Post by Shining Arcanine on 2009-09-08
I have VMWare Tools running on a Windows XP SP3 host and two Linux installations, Ubuntu 9.04 and the latest version of Gentoo Linux, setup as guests.

I have things configured such that I can SSH into both Ubuntu Linux and Gentoo Linux via a SSH client my university gave me. I assume I can SSH from one of them into another via a terminal. I have KDE configured on Gentoo such that I can type startx into a terminal and KDE opens in the virtual PC's monitor.

I would like to initiate a remote X session, logging to KDE on Gentoo Linux from Gnome on Ubuntu Linux, with KDE appearing in a window in my Gnome Desktop Environment on Ubuntu Linux. How do I do this?

---

### Post by suffice on 2009-09-09
From what I think you can just do a remote desktop from one to the other with vnc.

Or when you log into the ssh session from gnome to kde you can use an -X flag.   (ssh -X user@kdeIP) then use startx on the command line from there might work.

let me know.

---

### Post by jpkotta on 2009-09-09
I use this script.  It connects to an already running X server on the remote machine.  You need x11vnc on the remote machine, and some vnc client on the local one.

```

#!/bin/bash

usage="$0 [user@]remote_host [<DISPLAY>]"

login="$1"
if [ -z "$login" ] ; then
    echo $usage
    exit 1
fi

disp="$2"
if [ -z "$disp" ] ; then
    disp=:0
fi

ssh "$login" "x11vnc -localhost -display '$disp' -scale 4/5 -bg" 
vncviewer -via "$login" localhost"$disp"

```

---

