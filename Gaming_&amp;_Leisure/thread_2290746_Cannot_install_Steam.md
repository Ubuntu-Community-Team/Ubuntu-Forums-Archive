---
title: "Cannot install Steam"
date: 2015-08-14
forum: Gaming &amp; Leisure
---

### Post by Free_Nutella on 2015-08-14
I get this:

freenutella@Illuminati:~$ apt-get install steam
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by QIII on 2015-08-14
Moved to its own thread from [http://ubuntuforums.org/showthread.php?t=2217937](http://ubuntuforums.org/showthread.php?t=2217937)

The correct command is:

```
sudo apt-get install steam 
```

You will be prompted for your password.  Enter your password and press enter.  Nothing will be shown on the screen.  Not even asterisks.  This is normal.

---

