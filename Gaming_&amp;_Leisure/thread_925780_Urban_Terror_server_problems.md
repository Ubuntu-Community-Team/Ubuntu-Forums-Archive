---
title: "Urban Terror server problems"
date: 2008-09-21
forum: Gaming &amp; Leisure
---

### Post by rerendered3 on 2008-09-21
Whenever I try to start a LAN server in Urban Terror (installed from PlayDeb) the game freezes, badly. I wish I had terminal logs of this but the game takes down the system with it.

any ideas?

---

### Post by eenofonn on 2009-02-11
> **rerendered3 said:**
> Whenever I try to start a LAN server in Urban Terror (installed from PlayDeb) the game freezes, badly. I wish I had terminal logs of this but the game takes down the system with it.

any ideas?

something you might want to look into is running a dedicated server.  you can find the instructions at the link below....

[http://www.urbanterror.net/new_urt_manual/#SERVER_SETUP_.26_ADMINISTRATION](http://www.urbanterror.net/new_urt_manual/#SERVER_SETUP_.26_ADMINISTRATION)

and then if you want the server to not broadcast on the internet just change the options in the start.sh script to look like the one below

ioUrTded.i386 +set fs_game q3ut4 +set dedicated 1 +set net_port 27960 +set com_hunkmegs 128 +exec server.cfg


... hope that helps

-eenofonn

---

### Post by mr_niceguy on 2009-05-13
If you are launching the server from the graphical menu set "Dedicated" to "No" (not "LAN")

A dedicated server does not run the client.

---

### Post by SP3edy28 on 2009-09-21
Did u made it work?

---

