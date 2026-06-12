---
title: "Starting Gnome from a shell"
date: 2008-04-23
forum: Desktop Environments
---

### Post by seattle vic on 2008-04-23
I travel a lot, but keep in touch with my Ubuntu machines via putty and vncserver.  Occasionally I have to reboot, or restart Gnome.  So, when I do that I lose my connection and can reconnect to a shell.  However, Gnome has not started as I'm not at home to log in.  How do I get X and Gnome up from a shell???

Thanks  in advance,

Vic

---

### Post by blizz123 on 2008-04-23
startx command?

---

### Post by hariprs on 2008-04-23
If X is already running in your computer then you can simply start the vncserver from the shell using the cmd $vncserver, then you can use vnc client to connect to your computer.

If gnome session or X is not started already then try the following  command before starting vncserver
1) To start gnome
$ sudo gdm start

or

$ gnome-session& <<-- For this you need X to be running.

2)To start X
$ startx

---

