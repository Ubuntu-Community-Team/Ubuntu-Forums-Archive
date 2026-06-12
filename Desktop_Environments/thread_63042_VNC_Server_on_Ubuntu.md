---
title: "VNC Server on Ubuntu"
date: 2005-09-06
forum: Desktop Environments
---

### Post by seethru on 2005-09-06
I'd like to setup a VNC Server on my desktop at home, and use a web client through a browser to access it. Is there any open source solution which will accomplish this? I'm looking for something that I can access my desktop as I left it at home, and not login like a new user.

Any help is greatly appreciated.

---

### Post by evilghost on 2005-09-06
System -> Preferences -> Remote Desktop -> Sharing

That is your VNC Server, but I am not sure if it's listening on 5900 TCP for the HTTP daemon part, so a client executable may be required to connect. ;)

---

### Post by cwaldbieser on 2005-09-06
[QUOTE=seethru]I'd like to setup a VNC Server on my desktop at home, and use a web client through a browser to access it. Is there any open source solution which will accomplish this? I'm looking for something that I can access my desktop as I left it at home, and not login like a new user.

Any help is greatly appreciated.[/QUOTE]
If the built in "vino" doesn't offer a web client, "tightvnc" from the repositories does.

---

### Post by er4z0r on 2005-09-16
I may be wrong, but I think the built in vino-server only works when you are logged in with GNOME.

So if you just boot your box but do not login --> no vino-server :(

Is there a way to make vino-server start independent from a gnome login-session?

hIf not: which vncserver can accomplish this?

regards,
Til

OK. I am using freenx now. It's really damn fast. Wiki-Guide worked all fine

---

