---
title: "vncviewer (over ssh to xfce) control and alt keys not working"
date: 2017-02-01
forum: Desktop Environments
---

### Post by Slatevine on 2017-02-01
Im using vncviewer over ssh with xfce on the remote server which is running ubuntu 14.04.

Neither the CTL or ALT keys have eny effect at all (menus, terminal ... pressed alone or with another key (eg CTL C), or CTL S to save in Gedit).

Where do I look to get these keys working?



I start up VNC like this

```

ssh -L 5901:127.0.0.1:5901 -N -f -l myuser Myserver
vncviewer localhost:5901

with vnc configured with XStartup containing:
startxfce4 &

```

Can someone shed some light on this please? It's a hard life without the CTL key!

thanks 

:-)

---

### Post by Slatevine on 2017-03-15
Im still struggling with this problem, has anyone got any tips or solutions?

The high level summary is I cant use any control or alt key presses or combinations over my remote vnc session. All key presses have no effect whatsoever.

Any help, or even clues, appreciated. Ive looked around in key bindings and elsewhere to no avail.

---

