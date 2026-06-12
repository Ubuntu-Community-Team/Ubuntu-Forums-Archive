---
title: "Why is my system acting strange after I changed my hostname?"
date: 2006-09-22
forum: Desktop Environments
---

### Post by Svip on 2006-09-22
Ever since I changed my hostname (correctly) sudo has been acting strangely.  And I can't start up gksudo, it just... fails.

Here is the output from sudo:
```
$ sudo apt-get upgrade
sudo: unable to lookup new-zealand via gethostbyname()
```

This also means I can't use some of the cool features.  And I have to start a lot from terminal AND sometimes it won't even start the terminal from the menu.

Thanks in advance.

---

### Post by Jussi Kukkonen on 2006-09-22
> Ever since I changed my hostname (correctly)...
Some details about that might be useful. I guess you changed */etc/hostname*. Did you remember to edit */etc/hosts*?

---

### Post by ayoli on 2006-09-22
yes, i guess you have to reboot in recovery mode and edit /etc/hosts to have a line like this:
```
127.0.0.1 localhost new-zealand
```
assuming new-zealand is your new hostname.

---

