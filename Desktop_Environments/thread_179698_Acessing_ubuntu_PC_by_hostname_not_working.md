---
title: "Acessing ubuntu PC by hostname not working"
date: 2006-05-20
forum: Desktop Environments
---

### Post by hxx4 on 2006-05-20
I have multiple computers on my wired home network. Most of them are Windows XP, but I have a PC setup with ubuntu 5.10 (latest updates) which I use as a server. I can access this computer by using its local static IP address (192.168.0.12), but I am unable to access it by using its hostname (ubuntu). This comes after I installed and configured the Firestarter firewall. When I disable the firewall, the hostname starts working again. _So what I'm asking about is how to configure firestarter so that it allows requests by hostname over the local network._

**My current firestarter configuration is:**
Inbound traffic policy ports allowed:
-FTP (20-21)
-Samba (137-139 445)
-HTTP (80)
-HTTPS (443)
-Unknown (32000-33000) - I've found that opening these ports allows Windows networking to work fully (otherwise it didn't)
-VNC (5900-5901)
-XWindows (6000-6015)

I also have ICMP filtering enabled.

If there are any ports or ICMP packets I need to allow, I would greatly appreciate the help.

Note: I have encountered this hostname problem on multiple computers on different networks with virtually the same configuration.

Thanks!

---

### Post by cgjones on 2006-05-20
I would disable ICMP filtering completely. Unless you are really worried about scans and DOS attacks.

---

### Post by jones_jj on 2006-05-21
hxx4, I'd leave ICMP filtering on to keep looking at unauthorized echo requests, but I'd allow port 7 through.  This should allow passthrough by hostname.

> Unknown (32000-33000) - I've found that opening these ports allows Windows networking to work fully (otherwise it didn't)

Now this one I really don't understand.  Ports 137-139, and 445 all on TCP should allow windows networking to work just fine to your server, especially 445 which is the SMB port for Windows.  What are ports 32000 - 33000?  Are they on TCP or on UDP?

---

