---
title: "Install help vnc"
date: 2009-01-03
forum: General Help
---

### Post by majikhotline on 2009-01-03
hello unbunt country,

I'm a newbie that's looking for some program installation help.  I download real vnc and i don't know how to install it.  Do i have to compile or is there an easier install cause im not see it.  Please let me know what kind of info you need me to post.  thanks!

---

### Post by Cyclops_ on 2009-01-03
Are you looking for Server or Client or both? (something to view with, or to be seen with?)

If you are looking for client, you can open Synaptic, and look for xvnc4viewer, and install that directly from the repository.  Then you can use it by pressing <Alt><F2> and entering :
vncviewer [IP or HOST_NAME]<Enter>

If you are looking for the Server, you already have "Remote Assistance" installed...

At least that's the program that I use.  And fairly simple.

Thanks!

---

### Post by majikhotline on 2009-01-03
does the remote assistance work with windoze

---

### Post by Cyclops_ on 2009-01-03
Sure.  If you install a VNC Viewer on Windoze.  Like RealVNC ;)

---

### Post by majikhotline on 2009-01-03
i tried remoting and the windoze machine is not in the linux domain to pick it up and on the windoze i do have real vnc server and viewer on it.

---

### Post by Cyclops_ on 2009-01-04
Are they on the same network?  Do you have both IP addresses?  Do they have to go through a router to talk to each other?  You may have to open router ports (5900 by default)....

---

### Post by majikhotline on 2009-01-04
yes they are connected to the same switch. but they are not on the samr domain, port is open for vnc to connected to.

---

### Post by ugm6hr on 2009-01-04
Just to clarify - you are using Ubuntu (Gnome) desktop version?

---

### Post by majikhotline on 2009-01-04
yes I'm using ubuntu gnome

---

### Post by Cyclops_ on 2009-01-04
Well of course the 2 computers need to be able to talk somehow (you need to have a route between the two)....  whether that's getting them on the same network, I don't know...  I haven't worked too much on the networking side of things..

---

