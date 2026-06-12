---
title: "fsprotect aufs breaks network support"
date: 2009-11-05
forum: Desktop Environments
---

### Post by jesbecker on 2009-11-05
All,
   I am trying to build a protected desktop image for use in an educational environment. I have tried both Lethe and fsprotect on the Karmic operating system. The issue I am running into is that network support seems to be lost when using lethe or fsprotect. The gui network-manager gets stuck in the spin wheel state and using sudo dhclient in terminal gives:
dhclient:  error while loading shared libraries:  libc.so.6: cannot open shared object file:  No such file or directory.

The file exist and is readable on /lib/libc.so.6
With fsprotect active, the real root file system is mounted as readonly (/fsprotect/system). The aufs file system is mounted as /.

Booting with fsprotect turned off restores network connectivity.

Could this be do to networking and libaries being loaded from the real file system prior to the fsprotect scripts running and remounting as aufs?

Anyone have work around or fix?

---

### Post by EarlM on 2009-11-19
See this thread for the same kind of issue (no fix yet):
[http://ubuntuforums.org/showthread.php?t=1220145](http://ubuntuforums.org/showthread.php?t=1220145)[URL="http://http//ubuntuforums.org/showthread.php?p=8350565"]
[/URL]

---

### Post by jesbecker on 2009-11-19
> **EarlM said:**
> See this thread for the same kind of issue (no fix yet):
[http://ubuntuforums.org/showthread.php?t=1220145](http://ubuntuforums.org/showthread.php?t=1220145)[URL="http://http//ubuntuforums.org/showthread.php?p=8350565"]
[/URL]

I found the fix. You have to remove apparmor. It does not work with stacked file systems.

---

