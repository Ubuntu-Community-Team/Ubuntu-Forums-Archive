---
title: "ubuntu desktop vs ubuntu server"
date: 2009-01-07
forum: General Help
---

### Post by kr651129 on 2009-01-07
This may be a stupid question but here it goes.  It seems best for what I'm using my PC for to use ubuntu server with a gui.  That being said, are all the drivers and hardware support that is built in ubuntu desktop the same as server?  The reason I ask is Im currently running ubuntu desktop 8.04 and my internal wireless card worked out of the box.  Will this be supported under the server edition with no additional install?

---

### Post by whoop on 2009-01-07
If I understand you correctly you currently have a ubuntu desktop which works properly (enough), but you want to replace this with an ubuntu server (with a GUI)?

First of all installing a GUI on a server is unwise, mainly for performance and security reasons.

However, if you wish to take that path anyway I still can't think of a reason to wipe your current setup and install a server edition.

Why? you might ask:
Basically any service (that can be) provided on the server edition you can install on your current desktop using synaptic or apt-get.
The server edition lets you run mailserver, webserver, databaseserver, samba, ssh etc.
Nothing is stopping you from installing this to you're current installation.

Basically the server edition is just a stripped desktop edition (not literally probably, but you catch my drift).


Hope this helps.

---

### Post by cariboo on 2009-01-07
> Basically any service (that can be) provided on the server edition you can install on your current desktop using synaptic or apt-get.
The server edition lets you run mailserver, webserver, databaseserver, samba, ssh etc.
Nothing is stopping you from installing this to you're current installation.

I agree with whoop if you don't feel comfortable without a gui then just use your desktop as a server, all the services work just as well on the desktop version as they do on the server version, the only thing you might miss out on, is that the 32bit server kerenl can access more than 4Gb Ram.

If you are using the 64bit version you are OK to access more 4Gb ram.

Jim

---

### Post by sameat on 2009-01-07
I think you're getting decent advice, but I would also add that I wouldn't ever be excited about running any server over wireless.  The security issues can be dealt with if you are conscientious about it, but wireless performance may not be great for some server applications.

Like I said, the other advice you've gotten is good...if you're going to run a gui anyway, you might as well avoid the hassle of a rebuild.  My guess is that your wireless will be a bigger bottleneck than any extra desktop services running on the machine.

Good Luck!

---

### Post by kr651129 on 2009-01-08
Well here's the thing, and my thinking may be @$$ backwards so if it is please let me know.  I already have a server on a desktop hard wired into the router.  No GUI for security and I'm quite comfortable with the command line.  The reason I want the server edition with a GUI on my laptop follows the following thought process:

I'm trying to streamline my laptop as much as possible so I figure install the server with no desktop, apt-get xfce, and because I write code the build will have the build tools I need on it and hence leaving me with no over head packages.

If I'm totally off base here point me in the correct optimization process.  Thank you!

---

### Post by kr651129 on 2009-01-08
*bump*

---

### Post by SunnyRabbiera on 2009-01-08
well many have installed stuff like gnome on the server edition to get a GUI to be sure, its easy to do if you install gnome desktop via apt...
Apt is universal
the reverse is also true

---

