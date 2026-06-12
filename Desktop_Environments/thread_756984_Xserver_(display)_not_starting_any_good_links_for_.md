---
title: "Xserver (display) not starting any good links for troubleshooting this?"
date: 2008-04-16
forum: Desktop Environments
---

### Post by hoist1138 on 2008-04-16
hello all, good day.
here are my specs..

*  Motherboard: Soyo SY-KT333 DRAGON Ultra Platinum Edition (SY-KT333DU-P)
* chipset: VIA Apollo KT333
* processor: Athlon XP

* Leadtek WinFast A250 Ultra TD GeForce 4 Ti-4600
* Nvidia 4th-generation 256-bit GeForce4 Ti 4600 GPU 

I have tried BOTH Ubuntu Server 7.10 and now currently Ubuntu 6.06.2 Server
My goals are to get the Gui up and running so I can get samba running so I can use the raid across the network on the Ubuntu machine.

But display is a show stopper, I know this common issue for begginers like me, is there any great links or resources any of you seasoned ubuntites can suggest, by the way, even with all these config issues I still think all this is worth it, it is exciting times we are living in.

---

### Post by hoist1138 on 2008-04-16
by the way I have installed Gnome Gui and it ALMOST gets to the desktop GUI.
then spits out " cannot stat /etc/X11/X (no such file or directory), aborting
connection refused (errno 111): unable to connect to x server
no such process (errno 3): server error.

---

### Post by kshane on 2008-04-16
> **hoist1138 said:**
> by the way I have installed Gnome Gui and it ALMOST gets to the desktop GUI.
then spits out " cannot stat /etc/X11/X (no such file or directory), aborting
connection refused (errno 111): unable to connect to x server
no such process (errno 3): server error.

I was under the impression that the server editions did *NOT HAVE* a GUI...

Kevin

---

### Post by hoist1138 on 2008-04-16
your correct that it doesnt have it installed. but it is easily installed if you want, it just comes pre-configured for server environment, if someone wants to correct me on this please do so, but that is what I have learned...

---

### Post by warp99 on 2008-04-16
You can run the gnome-desktop on the server, but you have to install a desktop kernel since it includes additional modules that server kernel does not. All of your server applications will run fine on a desktop kernel. So install a desktop kernel first, then install the ubuntu-desktop.

Edit:
That's correct the server does not include a desktop because it's a security risk.

---

