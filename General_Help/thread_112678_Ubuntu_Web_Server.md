---
title: "Ubuntu Web Server"
date: 2006-01-04
forum: General Help
---

### Post by Jedeye on 2006-01-04
Hi, Im some what new at linux/ubuntu and was wondering if anybody knew of any good guides/tutorials for setting up a linux/ubuntu system to be a web server. I would eventualy like to get MySQL and PHP running on it as well, but one step at a time would probably be best ;) 

Thanks!

---

### Post by xequence on 2006-01-04
From what ive heard, people seem to aggree that Debian is a better server OS. I dont know why, as ubuntu is extremly similar, but still its what they say.

---

### Post by sciurus on 2006-01-04
Try searching the forums for LAMP.

---

### Post by melfyk on 2006-01-04
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-database-server]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-database-server")
;)

---

### Post by Tal on 2006-01-04
apt-get install apache2
apt-get install mysql-server

That should work for you right?

I used that with my MythTv install to get the basics setup.

---

### Post by domino on 2006-01-04
On one of my installs I use the following how-to. It's really great as far as configuring a DIY hosting server and running multi-domain server for development purposes. I would not however run Ubuntu as a production web server. 

> This is a detailed description about the steps to be taken to setup a Ubuntu based server (Ubuntu 5.10 - Breezy Badger) that offers all services needed by ISPs and hosters (web server (SSL-capable), mail server (with SMTP-AUTH and TLS!), DNS server, FTP server, MySQL server, POP3/POP3s/IMAP/IMAPs, Quota, Firewall, etc.).

[http://www.howtoforge.com/perfect_setup_ubuntu_5.10](http://www.howtoforge.com/perfect_setup_ubuntu_5.10)

---

### Post by briancurtin on 2006-01-05
all of the above is good, or you could even look in the server area of this site...

---

### Post by Jedeye on 2006-01-05
Thanks all! I will get busy :smile:

---

