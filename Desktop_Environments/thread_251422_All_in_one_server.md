---
title: "All in one server"
date: 2006-09-05
forum: Desktop Environments
---

### Post by traacer on 2006-09-05
I'm running ubuntu 6.06 server with the ubuntu desktop. I want to run apache2, proftp, promail, dhcp and bind.  I have a static ip, and registered domain name.  I've been trying to get it all to run on 1 machine, but with no luck.  When it comes to bind, i have no idea what i'm doing.  the machine is a amd athlon 3000, 512mb ddr, msi kt6v mobo. with a addon ide card, and additonal network card.  The onboard ethernet has the static ip, the add on card is for the internal network.  I have an external ip of 71.241.102.71, that i want to use as the domain traacer.org.  The internal is 192.168.1.96.  I have samba already running and sharing files internally.  Thanks for the help!](*,)

---

### Post by alecjw on 2006-09-05
This is the wrong place for this post really - should be in the server talk forum, but here are some answers. I can't help you with everything but i can with apache2, dchp and proftp. Well, not quite. I reccomend vsftpd (very secure ftp daemon) instead of proftp. So here's some nice juicy code:
```
sudo aptitude install apache2 dchpd vsftpd
```
There's a very nice gude to configuring and using vsftpd at help.ubuntu.com.

---

### Post by homegrown on 2006-09-05
You could also try djbdns -- I found it quite easy to configure.

---

