---
title: "Need an FTP Server that works with Ubuntu"
date: 2009-05-07
forum: General Help
---

### Post by Smacky311 on 2009-05-07
Does anyone know of an FTP Server that actually works with Ubuntu?

I have tried vsftpd 2.0.6 and it worked for about an hour then started giving me an error Connection attempt failed with "ECONNREFUSED - Connection refused by server".

I found it was a bug and needed to upgrade to 2.0.7.  I tried doing the make -f for the makefile and it gave me an error.

So I gave up on vsftpd and went to twoftpd.  This program doesn't let me connect from the command line and I don't know where and if it has a config file of some kind.  The documentation I've found is useless

---

### Post by mixmaster on 2009-05-07
wu-ftpd or proftpd depending on the feature set you need?

Both are in the ubuntu repositories.

---

