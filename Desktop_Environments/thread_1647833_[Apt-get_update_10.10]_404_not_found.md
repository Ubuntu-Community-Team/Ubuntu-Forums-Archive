---
title: "[Apt-get update 10.10] 404 not found"
date: 2010-12-17
forum: Desktop Environments
---

### Post by Doggins on 2010-12-17
This seems strange to me since this is a relatively fresh install and I haven't touched the repo's
I'm running 10.10 64bit, and this was working fine yesterday

```
W: Failed to fetch http://ppa.launchpad.net/shiki/mediainfo/ubuntu/dists/maverick/main/binary-amd64/Packages.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/shiki/mediainfo/ubuntu/dists/maverick/main/binary-amd64/Packages.gz  404  Not Found
```I'd appreciate any help you can offer :KS

---

### Post by wojox on 2010-12-17
Maybe their fixing something if it worked yesterday on Maverick, but it doesn't exist now. 

[http://ppa.launchpad.net/shiki/mediainfo/ubuntu/dists/](http://ppa.launchpad.net/shiki/mediainfo/ubuntu/dists/)

---

### Post by bobcollard on 2010-12-18
Open Software sources and make sure you have "Download from: Main Server" selected.  Then on the second tab check the boxes that apply to the mirrors you want to use.  Close Software Sources and run Terminal:
```
sudo apt-get update
```

---

### Post by Doggins on 2010-12-18
alright so i changed it from canada to main and now i get this
```
Failed to fetch http://ppa.launchpad.net/shiki/mediainfo/ubuntu/dists/maverick/main/binary-amd64/Packages.gz  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by bobcollard on 2010-12-18
> **Doggins said:**
> alright so i changed it from canada to main and now i get this
```
Failed to fetch http://ppa.launchpad.net/shiki/mediainfo/ubuntu/dists/maverick/main/binary-amd64/Packages.gz  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```
Just checked, they do not have Maverick on their list, uncheck it in Software sources.  See screenshot.

---

### Post by Doggins on 2010-12-18
awesome thanks!

---

### Post by bobcollard on 2010-12-18
You are welcome.  While this did not really "solve" the problem I hope it is resolved to your satisfaction.  Just know that this is an ongoing problem of the right hand not knowing what the left is doing.  A miscommunication has gone by and it may or may not be fixed.  That's why I said uncheck it, you might try it again some day and find you have that link.  Good luck.

---

