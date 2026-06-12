---
title: "[SOLVED] Fixing Ubuntu Upgrade"
date: 2008-10-27
forum: Development CD/DVD Image Testing
---

### Post by bprof on 2008-10-27
Hello,

After upgrading to 8.10 I failed to have the system work normally, I've been trying to fix the installation but I'm getting this error

Try: dpkg --configure -a to fix

When I tried the command in the message it didn't work.

apt-get upgrade
apt-get dist-upgrade 

Failed and gave the same error.

A sample of error messages I get when I ran dpkg --configure -a is like the following:
dpkg; error process totem (--configure):
Errors were encountered while processing:
dbus
rhythmbox
ha1
...

Any help?

Thanks

---

### Post by howefield on 2008-10-27
try preceding your command with sudo eg,

```
sudo dpkg --configure -a
```

---

### Post by bprof on 2008-10-27
I did already, but it didn't work.

---

### Post by bprof on 2008-10-28
Any help?

---

### Post by bprof on 2008-10-28
I found the solution in this post, many thanks to the poster:
[http://ubuntuforums.org/showthread.php?p=6049930#post6049930](http://ubuntuforums.org/showthread.php?p=6049930#post6049930)

---

