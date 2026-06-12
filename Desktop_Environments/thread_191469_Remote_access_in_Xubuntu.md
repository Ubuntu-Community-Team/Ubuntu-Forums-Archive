---
title: "Remote access in Xubuntu"
date: 2006-06-07
forum: Desktop Environments
---

### Post by jrobinson5 on 2006-06-07
I have an ubuntu server that I keep in a closet and access remotely. I used to be running plain Ubuntu breezy, which had an option to enable remote access. But I just upgraded to Xubuntu Dapper (BTW xfce is SO much faster than gnome with a 466 mhz processor) and now I can't find where the option to enable remote access is. Did I overlook something obvious? Also, how do I have it auto-login?

---

### Post by Ramses de Norre on 2006-06-07
By vnc? Do ```
vino-preferences
``` to configure it, it's somewhere in the menu too but I don't know the name. If you mean by ssh you might need to install that.

---

### Post by jrobinson5 on 2006-06-07
Yes, VNC. Whenever I type in that command, I get bash:vino-preferences:command not found

---

### Post by Ramses de Norre on 2006-06-07
Ow hmm I just see it's a gnome tool, you could install the vino package or maybe there is a vnc server in xfce by default too but I don't know where.

---

### Post by jrobinson5 on 2006-06-07
OK I did a sudo apt-get install vino and then a vino-preferences and that did the trick. Thank you. Also, how do I auto-login? (should I start a new thread?)

---

### Post by Ramses de Norre on 2006-06-07
Auto login local into xfce? Do you use gdm? If so ```
gksudo gdmsetup &
``` (sorry, I don't know the menu entries)
There probably is a similar way for kdm (or which ever you're using).

---

### Post by jrobinson5 on 2006-06-07
I don't know whether I use gdm or kdm, I'm just using the regular xubuntu install. And I installed vino and opened vino-preferences and allowed remote access, but it's not working. I get:
jrobinson@laptop:~$ vncviewer 192.168.1.106
VNC viewer version 3.3.7 - built Feb 20 2006 12:04:05
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server
jrobinson@laptop:~$

---

### Post by jrobinson5 on 2006-06-07
I'm just using a regular xubuntu install. So I just installed ubuntu-desktop and vino works fine from within gnome, but not xfce.

---

### Post by Ramses de Norre on 2006-06-07
I never used vnc before.. so it can't help you with that.. I just knew the command=)
cat /etc/X11/default-display-manager will show which display manager you're using.

EDIT: you might need to run /usr/lib/vino/vino-server or /usr/lib/vino to start the vino server in xfce.

---

