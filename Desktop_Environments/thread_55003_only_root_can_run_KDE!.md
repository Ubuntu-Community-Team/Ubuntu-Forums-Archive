---
title: "only root can run KDE!"
date: 2005-08-07
forum: Desktop Environments
---

### Post by coogor on 2005-08-07
Hi,

I did a full upgrade to KDE 3.4.2 using the packages from the KDE-Website.
After this, only root can run KDE.
For a normal user, the X-Server starts, and when displaying the (first) white screen, it terminates. On the console, there is nothing unusual.
I assume there are access-problems with the permissions, but no idea on which files.

Any ideas?

TIA!

---

### Post by whoiam55 on 2005-08-07
does it come back to shell when crash ? login as user into shell and try sudo /etc/init.d/kdm restart, hope it should ask you username/password to login, try login and tell if it spit any error

---

### Post by coogor on 2005-08-07
it comes back to shell, and If I log in as proposed it starts KDM. After login on the (graphical) login screen the same as described happens. No further messages are displayed.

---

### Post by BanskuZ on 2005-08-07
Try chmoding:
.ICEAuthority
.kde
.kde/*

---

### Post by coogor on 2005-08-07
Changed the authorisations (I assume you meant /home/user/.kde etc) to rw for all, but did not help

---

### Post by geearf on 2005-08-07
I had this problem once and the reason was very special.


In fact, I had just lost the rights to write on /tmp/, you can look at this also.

---

### Post by coogor on 2005-08-12
A good hint, thanks, but all permissions on /tmp are OK. Even after deleting all content of /tmp it did not work...

---

### Post by apokryphos on 2005-08-12
[QUOTE=coogor]Hi,

I did a full upgrade to KDE 3.4.2 using the packages from the KDE-Website.
After this, only root can run KDE.
For a normal user, the X-Server starts, and when displaying the (first) white screen, it terminates. On the console, there is nothing unusual.
I assume there are access-problems with the permissions, but no idea on which files.

Any ideas?

TIA![/QUOTE]
Best to chown. 

chown -R username:username ~/.kde ~/.config

---

### Post by coogor on 2005-08-15
> 
Best to chown.

chown -R username:username ~/.kde ~/.config

Hmm...did not work. I created a new user with the same effect.

By this I noticed a different error-meesage: device full! No space left on the root-partition!  ](*,) 

Maybe due to the 'big' upgrade to KDE 3.4.2? Is apt caching the installation files somewhere? What else then /tmp /var/tmp /var/log can be deleted?

---

### Post by coogor on 2005-08-16
Ok, cleaned the apt-cache, and now some xxx-MB are available.

But this does not fix the problem.....

---

