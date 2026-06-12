---
title: "Ubuntu without a monitor"
date: 2009-02-13
forum: General Help
---

### Post by challaire on 2009-02-13
I recently installed Ubuntu 8.10 and everything works great when a monitor is connected to the box.  Once I disconnect the monitor the box always loads in low graphics mode and will not get beyond the "low graphics mode" message.  I would like to be able to boot without a monitor plugged into the system so that I can use a VNC viewer to access the box.  I can connect to the box via VNC if a monitor is plugged in.  Is there a way to disable low graphics mode?  The graphics card in the box is integrated in the motherboard.

---

### Post by HermanAB on 2009-02-13
Two things:
Do not use VNC, install ssh-server instead.  SSH can  do everything that VNC does and much more.  Secondly, run the server in runlevel 3 (init 3).  You do not need to run X if you use SSH for remote control.

Connect to the box like so:
$ ssh user@server gnome_panel

Cheers,

Herman

---

