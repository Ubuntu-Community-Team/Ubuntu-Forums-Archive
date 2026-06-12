---
title: "Official firefox 1.0.7 installation error"
date: 2006-01-13
forum: Desktop Environments
---

### Post by Goochi on 2006-01-13
Hi all,

I'm getting this error when I 'apt-get install firefox'.
```
Unpacking firefox (from .../firefox_1.0.7-0ubuntu20_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/firefox_1.0.7-0ubuntu20_i386.deb (--unpack):
 trying to overwrite `/usr/bin/firefox', which is the diverted version of `/usr/bin/firefox'
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_1.0.7-0ubuntu20_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

/usr/bin/firefox doesn't even exist. I do have firefox 1.5 but I just got that in my home folder, nothing on the system.

I really don't understand :???: anyone got an idea ?


Thanks a lot,
gOochi

---

### Post by cbudden on 2006-01-13
Try sudo apt-get update and try again, usually fixes most of those problems for me.

---

### Post by Goochi on 2006-02-05
I wish the solution was that easy, nono.. I've been stuck with this problem for a long time. No one else has an idea or suggestion ?

Thanks again.
gOochi

---

### Post by kaamos on 2006-02-05
Look at removing the diversion here: [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

