---
title: "Firestarter fails in Boot Menu"
date: 2009-04-10
forum: General Help
---

### Post by Gael33 on 2009-04-10
When I boot my computer usually get a list of files booting (POST) followed by ... OK. The only exception is the installed firewall (Firestarter) which shows ... Failed.
Now is this normal, because I have uninstalled Firestarter and reinstalled it several times and I still get "Failed" at startup? Oddly, Firestarter appears to be working normally when bootup is complete.

Duel Boot:-
Ubuntu 8.04 (64)
Windows XP Pro
PC is a HP Compac dx2250 Microtower.
AMD 64 Athlon 3800
2 Gig memory
ATI graphics

---

### Post by mb_webguy on 2009-04-10
Firestarter is not a firewall.  It's a GUI configuration tool for iptables, which is the Linux firewall.  You shouldn't be trying to start Firestarter during boot (or really at any time except when you want to reconfigure iptables), and it will *always* fail, since the graphical environment hasn't been loaded at that point.

Also, most people don't need to change the iptables, anyway.  Please check the links on security in Ubuntu in my signature.

---

### Post by ivanvajar on 2009-04-10
Just to confirm the post above. You don't need to start Firestarter. The actual firewall program is iptables that is running when Ubuntu is loaded. Firestarter is just graphical environment to configure iptables if needed (most people don't need to configure it).

---

### Post by bodhi.zazen on 2009-04-10
Firestarter has not been maintained since 2005 and as it is starting to show it's age.

I suggest you use ufw or if you want a gui gufw.

---

### Post by Gael33 on 2009-04-10
> **bodhi.zazen said:**
> Firestarter has not been maintained since 2005 and as it is starting to show it's age.

I suggest you use ufw or if you want a gui gufw.

As a relative newbie I had never heard of gufw ... what is it, and where can I get it as it's not in synaptic package manager.

Thanks, gael.

---

### Post by bodhi.zazen on 2009-04-10
gufw is in the repos as of Ubuntu 8.10

Otherwise : [http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

---

### Post by Gael33 on 2009-04-10
> **bodhi.zazen said:**
> gufw is in the repos as of Ubuntu 8.10

Otherwise : [http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

Thank you ... much appreciated :)

gael.

---

### Post by Gael33 on 2009-04-11
> **bodhi.zazen said:**
> gufw is in the repos as of Ubuntu 8.10

Otherwise : [http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)


A final question on this issue, I downloaded gufw and installed it ... it shows up as installed and everything is coming through as expected from the www. Q; Are the program default settings adequate for a "normal" user?

Thanks, gael.

---

### Post by 3rdalbum on 2009-04-11
The default setting of UFW (and gUFW by definition) is to block all incoming connections. This is the most secure that a firewall can be and it is appropriate for anybody who does not want to run an Internet-facing server.

---

### Post by Gael33 on 2009-04-11
> **3rdalbum said:**
> The default setting of UFW (and gUFW by definition) is to block all incoming connections. This is the most secure that a firewall can be and it is appropriate for anybody who does not want to run an Internet-facing server.


Thanks for a quick reply ... 

gael

---

