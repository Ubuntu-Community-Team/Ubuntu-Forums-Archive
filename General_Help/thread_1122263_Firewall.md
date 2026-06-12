---
title: "Firewall"
date: 2009-04-10
forum: General Help
---

### Post by brampt1 on 2009-04-10
I installed Gufw, I have it set to deny incoming traffic. Do I actually need it?  I'm a home user.
Thanks

---

### Post by mb_webguy on 2009-04-10
Not really.  By default, no ports on Ubuntu are open, which means that no applications are listening.  A closed port is just as secure as a port stealthed by a firewall.  If you install some sort of server application, then they will listen on their associated ports.  But if you installed such software, you likely *want* them listening.

Basically, a firewall on a Linux desktop is only good if you want to install some kind of server but don't actually want to use it as a server.  For example, if you want to do web development, you could install Apache but stealth port 80 so other computers couldn't view your developmental web pages.

I'd suggest looking at the links on security in my signature before you go about changing the security settings on your system.  If you don't understand why things are the way they are, you may actually end up making it *less* secure.

---

### Post by brampt1 on 2009-04-10
> **mb_webguy said:**
> Not really.  By default, no ports on Ubuntu are open, which means that no applications are listening.  A closed port is just as secure as a port stealthed by a firewall.  If you install some sort of server application, then they will listen on their associated ports.  But if you installed such software, you likely *want* them listening.

Basically, a firewall on a Linux desktop is only good if you want to install some kind of server but don't actually want to use it as a server.  For example, if you want to do web development, you could install Apache but stealth port 80 so other computers couldn't view your developmental web pages.

I'd suggest looking at the links on security in my signature before you go about changing the security settings on your system.  If you don't understand why things are the way they are, you may actually end up making it *less* secure.



Thanks, I won't change anything. I thought it was secure as is.

---

