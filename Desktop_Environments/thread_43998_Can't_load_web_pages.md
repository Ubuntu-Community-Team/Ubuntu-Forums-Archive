---
title: "Can't load web pages"
date: 2005-06-24
forum: Desktop Environments
---

### Post by lgl on 2005-06-24
I have an adsl router set up that I know is set up correctly. (Another machine connects to Internet through it) But I cannot connect to the Internet throught my Linux machine. I have eth0 set up for dhcp and it recieves an ip address from the router. I can ping the router from my machine and I can ping my machinre from the router. I can also trace route through to the isps' dns server fine, so at one level the connection seems fine.

Mozilla will not connect to web sites taking a long time saying waiting for connection to ... Everything else also takes longer to load now that dhcp is configured.

Any ideas.

Thanks Leon

---

### Post by sickdude on 2005-06-24
if you can ping everything for example google.com then your connection is fine

check your browser or try another one (firefox)

---

### Post by lgl on 2005-06-24
I can ping servers over the Internet and I am using Mozilla Firefox. I can only think that I have some settings wrong somewhere that stop it using the router as a gateway.

Have just been over to the Mozilla site and have found that I need to look at the firewall and dns which may be causing firefox problems. Will let you know.

Thanks Leon

---

### Post by sickdude on 2005-06-24
lets hope you find it

maybe you can test it with a command line browser like "links" dont know if you can apt-get this but its worth a shot

---

### Post by lgl on 2005-06-24
found it - posting from Linux.

Went to Mozilla site and searched. Found that turning off ipv6 does the trick.

[http://forums.mozillazine.org/viewtopic.php?t=258042](http://forums.mozillazine.org/viewtopic.php?t=258042) if any one is interested.

---

### Post by sickdude on 2005-06-24
nice to hear that it works dude

thnx for letting it know

---

