---
title: "Changed hostname, now can't use sudo!"
date: 2006-07-16
forum: Desktop Environments
---

### Post by Schalken on 2006-07-16
I changed my hostname by executing ```
sudo gedit /etc/hostname
``` and replacing the old hostname with a new one (lovebox), saving, and restarting my computer.

Now when I try to do something in System -> Administration, it just closes, and when I try to run a command as root with sudo or gksudo it reports: ```
sudo: unable to lookup lovebox via gethostbyname()
```

I thought the easiest way to fix the problem would be to change the hostname back to what it was before, but I can't do that without sudo!

---

### Post by Schalken on 2006-07-16
Nevermind, recovery mode got it fixed! (I had never used it before and didn't know it would log you in as root) :D :D :D

---

