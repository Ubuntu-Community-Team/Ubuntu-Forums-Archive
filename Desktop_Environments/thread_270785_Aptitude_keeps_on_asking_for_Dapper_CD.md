---
title: "Aptitude keeps on asking for Dapper CD"
date: 2006-10-03
forum: Desktop Environments
---

### Post by ToniCipriani on 2006-10-03
I've installed Ubuntu Server on a Thinkpad 240Z using loadlin (the machine has no CD-ROM), and the server's up and running. However, now I have a problem with Aptitude. It keeps on asking me for the Dapper CD every time I try to install anything. But clearly, I can see it's actually downloading from the Ubuntu servers.

How can I change Aptitude so that it doesn't ask for the CD anymore?

Thanks!

---

### Post by Fass on 2006-10-03
Edit your /etc/apt/sources.list file and comment out the CD as a repo.

---

### Post by Sef on 2006-10-03
You comment out a line by putting a hash mark (#) before the line in question.

---

### Post by aysiu on 2006-10-03
Commented out: ```
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
``` Uncommented: ```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
```

---

