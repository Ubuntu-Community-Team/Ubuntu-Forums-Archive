---
title: "dovecot startup error - Cannot allocate memory?"
date: 2009-06-18
forum: General Help
---

### Post by peridot on 2009-06-18
Hello,

I just applied the latest patches, including the 2.6.28-13-generic kernel. Everything seems to work fine after the reboot, except "/etc/init.d/dovecot start" fails. It complains:

```
Jun 18 14:53:39 servername dovecot: Fatal: Auth process died too early - shutting down
Jun 18 14:54:21 servername dovecot: auth(default): dovecot-auth: error while loading
shared libraries: libgpg-error.so.0: failed to map segment from shared object: Cannot allocate memory
Jun 18 14:54:21 servername dovecot: child 8711 (auth) returned error 127

```Any ideas if this is from dovecot or elsewhere?

I'm running 64 bit 9.04 ubuntu
(uname -a: Linux servername 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:55:09 UTC 2009 x86_64 GNU/Linux )

Thanks for any help!

---

### Post by CCG121 on 2010-04-14
I am getting the same error on a 

sudo /etc/init.d/dovecot start

Warning: Last died with error (see error log for more information): Auth process died too early - shutting down

I have tried a couple of things i found while on Google none of them worked.

---

