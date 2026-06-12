---
title: "VideoLan and AMD64"
date: 2005-09-27
forum: Desktop Environments
---

### Post by cypher35 on 2005-09-27
howdy, this is probably an easily fixed problem, but i am still a bit new to this...

i am trying to set up video lan client on my amd64 setup.  I modified */etc/apt/sources.list* with the urls videolan.org suggested, but it appears that they do not support amd64 binaries...
```
Err http://download.videolan.org sarge/main Packages
  404 Not Found
Hit http://us.archive.ubuntu.com hoary-updates/restricted Sources
Hit http://download.videolan.org sarge/main Sources
Fetched 3B in 0s (4B/s)
Failed to fetch http://download.videolan.org/pub/videolan/debian/dists/sarge/main/binary-amd64/Packages.gz  404 Not Found
Reading package lists... Done
W: Couldn't stat source package list http://download.videolan.org sarge/main Packages (/var/lib/apt/lists/download.videolan.org_pub_videolan_debian_dists_sarge_main_binary-amd64_Packages) - stat (2 No such file or directory)

```

can i not just install a "binary-i386" package instead?  what are my options?

---

### Post by cypher35 on 2005-09-27
nevermind, i got it up and running...

i ended up using synaptic instead of apt-get and for some reason it showed up even though it's using the same sources list.  O_o

whatever, i'm happy

---

