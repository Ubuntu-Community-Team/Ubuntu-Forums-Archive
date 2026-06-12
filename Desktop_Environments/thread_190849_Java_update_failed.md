---
title: "Java update failed"
date: 2006-06-06
forum: Desktop Environments
---

### Post by spaceghoti on 2006-06-06
I have attempted to compile the latest java update directly from Sun as well as apt-get and automatix, but whenever I type java --version I get 1.4.2 rather than 1.5.  Frostwire gives Java errors on load, and Firefox occasionally locks up the system irretrevably (I can't even Ctrl-F2 to a terminal window).  Can anyone recommend a way for me to perform a clean install of Java without having to wipe my system again?

Thank you.

---

### Post by spaceghoti on 2006-06-07
Wow, a lot of people have created new threads.  Yikes!

---

### Post by spaceghoti on 2006-06-07
Well, what do you know?  It installed, but it didn't update the current java version.  The [UbuntuWiki](https://wiki.ubuntu.com/RestrictedFormats#head-6acdf8655644645c067fb9e965a66be38681b7fb) gave me the solution:  

```
sudo update-alternatives --config java
```

---

