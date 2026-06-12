---
title: "apt-get update failing"
date: 2005-09-29
forum: Desktop Environments
---

### Post by seaeric on 2005-09-29
When I run sudo apt-get update, I am getting some failures.  Here is what is failing. Could this be part of last weeks firefox issue?

Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


Thanks,
Eric

---

### Post by KingBahamut on 2005-09-29
Backports are down. 
cd /etc/apt
sudo nano sources.list
comment out the backports mirrors, DO NOT DELETE THEM. =)
Ctrl-X , say yes to save 
then run apt-get update 
and apt-get upgrade and you should be fine.

---

### Post by seaeric on 2005-09-29
Thanks! But at some point I'll have to remove the comments once they are backup, correct?

Eric

---

### Post by KingBahamut on 2005-09-29
Yeppers.

---

