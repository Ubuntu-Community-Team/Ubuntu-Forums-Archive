---
title: "How do I configure Ubuntu to share files on Gtk-gnutella?"
date: 2006-07-19
forum: Desktop Environments
---

### Post by randell6564 on 2006-07-19
Hey folks!

I use Limewire AND Gtk-Gnutella.  The thing is, I have over 800 files to share but never see any uploading activity.

I'm assuming that is because ubuntus' default is to not listen on any ports, so everyone is blocked from getting to my files.

How do I open a port for Limewire and Gtk-Gnutella?

Thanks!

---

### Post by Dubbayoo on 2006-07-19
Open Limewire and see which ports it uses for incoming connections. Then make sure those ports are open and/or NAT'ed from your firewall.

---

### Post by randell6564 on 2006-07-19
> **Dubbayoo said:**
> Open Limewire and see which ports it uses for incoming connections. Then make sure those ports are open and/or NAT'ed from your firewall.

Thanks, but the thing is, I dont no HOW to check which ports are open. And I am on the other side of a router.  I dont have a firewall on my box unless ubuntu comes with one which I dont think that it does.

Is there some commands that you can provide me with that I can use to check/open ports?

Thanks!

---

### Post by Dubbayoo on 2006-07-19
If you don't have a firewall then every port with a daemon listening on it is open. Running nmap against localhost will tell you for sure. As far as which port Limewire listens on I say again - open Limewire and take a look or read the docs. I'm not at a Linux box to tell.

---

### Post by randell6564 on 2006-07-19
> **Dubbayoo said:**
> If you don't have a firewall then every port with a daemon listening on it is open. Running nmap against localhost will tell you for sure. As far as which port Limewire listens on I say again - open Limewire and take a look or read the docs. I'm not at a Linux box to tell.

Thanks!  Limewire listens on port 39571, but my problem is, I dont know where to go or what to do in order to check if that port is open.

Dont know what "nmap" is or how to use it so I guess I'll look around for a while.

As far as "every port" being open, then that would mean I would have no problem sharing files but that is not the case.

Thanks again!

---

### Post by deivid_the_clown on 2007-11-08
Puedes probar aquí.

[http://www.canyouseeme.org/](http://www.canyouseeme.org/)

---

