---
title: "lock file??"
date: 2006-04-19
forum: Desktop Environments
---

### Post by zorlab on 2006-04-19
upon several operations I get perermission denied for the lock file

Exp:

```
barry@SCSI:~$ apt-get install XNC
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

```

Can I change file permissions for this file?  What is it for?

---

### Post by Qrk on 2006-04-19
You need to run apt-get with sudo.

```
sudo apt-get install XNC
```

The file is there for exactly that purpose... to only allow root to use apt-get.

---

