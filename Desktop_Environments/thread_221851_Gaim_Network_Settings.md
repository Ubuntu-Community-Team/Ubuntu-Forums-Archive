---
title: "Gaim Network Settings"
date: 2006-07-24
forum: Desktop Environments
---

### Post by Luke771 on 2006-07-24
Hi.

How do I configure Gaim 2.0 beta 3 to connect through a proxy server?

The Gaim version is the one that Automatix installed, I tried the Tools menu and went  to Preferences/Network but all I found was a field where I could specify STUN server, no proxy. I tried all the menus but I couldn't figure out *where* I'm suposed to specify the proxy server.

---

### Post by shuttleworthwannabe on 2006-07-24
I have  the same problem here. Hope someone could help? I have put the proxy settings in /etc/environment file so that sorat takes care of the other programs that try to access the web outside the proxy. But GAIM seems to not honor that (use environment settings).

---

### Post by firebadger on 2006-07-24
Is it not in the Accounts>Modify Account>Show More Options section?  I'm afraid I'm looking at an older version, so it's probably no help.

---

### Post by orb9220 on 2006-07-24
When I run gaim there is a preferences in login window when I click on that it brings up preferences.  Halfway down is network in the Network section is:

IP address
Ports
Proxy service

You are selecting in login window?
there are 3 buttons Accounts - Perferences - Sign On

---

### Post by Luke771 on 2006-07-24
OK I got it.
Here's the solution: Click Accounts, then Add/Edit, then select your accounts one at the time and click Modify, got to the Advanced tab and click on Use Global Proxy. There you can specify what kind of Proxy it is and what the IP and the port numbers are.

Thanks for these answers, they helped me figure it out.

---

