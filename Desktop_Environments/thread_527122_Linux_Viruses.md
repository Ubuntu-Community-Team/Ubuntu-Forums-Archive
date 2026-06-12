---
title: "Linux Viruses"
date: 2007-08-16
forum: Desktop Environments
---

### Post by feisty_fawn on 2007-08-16
Can Linux get infected by Windows viruses and spyware and is Linux quite hackable, like Windows or will I need a firewall and antivirus?

---

### Post by heimo on 2007-08-16
> **feisty_fawn said:**
> Can Linux viruses get infected by Windows viruses and spyware and is Linux quite hackable, like Windows or will I need a firewall?

If you're asking can Windows viruses infect Ubuntu, answer is no. And is Ubuntu completely secure, answer is also no. It's security can be cracked, and you should always keep your system up to date (there's update notifier that helps). However you do not need firewall in your standard Ubuntu install as there are no outside listening services running.

---

### Post by aysiu on 2007-08-16
> **feisty_fawn said:**
> Can Linux get infected by Windows viruses and spyware and is Linux quite hackable, like Windows or will I need a firewall and antivirus?
Read this:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by needhelpplease on 2007-08-16
There basically are no Linux viruses.  It's theoretically possible that there could be one, but none are in the wild, and for various reasons it is a lot harder to make a virus for Linux than for Windows.

---

### Post by Gremlinzzz on 2007-08-16
There are viruses in linux systems there called noobs just read the forum see how many systems they messed up.The one i check for is a rootkit but i never found one.:guitar:

---

### Post by Chaotic Thought on 2007-08-16
If you have a router, then that's a firewall; I think you definitely should have that, no matter the system. For example, I recently was using VNC to allow a friend and I to share a desktop screen on the phone. Anyway, after I was done, I looked in the logs and there were lots of login attempts that were trying random passwords to try and get into my VNC server.

Software firewall on Linux is called iptables. You can search for this on the Internet and find some tutorials.

For Linux viruses: it's always possible but there are no known Linux viruses in the wild. But trojans are possible--someone could send you a doctored program designed to open up your system--for example if someone random emails you and says "Hey install this cool DEB I found" then you should probably say "No thanks"

---

### Post by vexorian on 2007-08-16
I once tried running a windows virus with WINE. ...WINE crashed

edit: Something some users skip is the fact that the user that installed the system got sudo privilege, however "normal" users should not really have it. So if you set the system up for more people than you it might be a good idea not to give them sudo prileges .

---

### Post by misfitpierce on 2007-08-16
I believe its possible for some windows viruses to mess up the Wine directories... but in that case you can manually delete the wine directories and reinstall wine as if it were clean installing windows :) Not 100% sure. But to affect Ubuntu directly... No

---

### Post by Kilz on 2007-08-16
If you feel the need to install some anti virus because of some reason no one has thought up. At least don't pay for it.

---

### Post by genecyst on 2007-08-16
you can always install [ClamAV]("http://www.clamav.net/") to be on the safe side. I use it on my main samba server.

---

### Post by cmat on 2007-08-16
The real threat is getting hacked. The password is one of the most important security features you have. Make sure it's long and contains lower an upper case letters along with some number and even characters like #$%&. 

Like: #edS6rev$

That thing will take for ever to be brute forced, also change it ever so often. 

But make sure you have some sort of hardware firewall like a router for even greater protection. It can also be set not to accept pings, this will protect your system from being hosed via DDoS attacks.

---

