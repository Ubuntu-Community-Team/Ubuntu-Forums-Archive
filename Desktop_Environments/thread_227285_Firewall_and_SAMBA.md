---
title: "Firewall and SAMBA"
date: 2006-08-01
forum: Desktop Environments
---

### Post by Frihet on 2006-08-01
Is there a resource I can draw upon to setup the standard Ubuntu firewall so that SAMBA will work? I have Firestarter installed, as well. I would like to do the setup through Firestarter -- if I can.

Thanks!

---

### Post by simonn on 2006-08-01
Maybe looking at the "Using a firewall" section of the Official Smaba How-to might help...

[http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/securing-samba.html#firewallports](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/securing-samba.html#firewallports)

---

### Post by scxtt on 2006-08-01
you should be able to just allow access from the IP of the box you're using samba with (that's all i ever had to do) ... you can allow the samba ports, but i found it easier to just allow any host that was on my network (cause i'm the only one who uses them ;)) ...

---

### Post by Frihet on 2006-08-02
Good idea. Sometimes things can be simple. I'll try this.

---

