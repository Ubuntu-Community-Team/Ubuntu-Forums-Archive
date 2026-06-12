---
title: "kubuntu desktop instlalation failed"
date: 2008-01-13
forum: Desktop Environments
---

### Post by kaiwan on 2008-01-13
I have ubuntu gutsy, and tried to install kubuntu-desktop.
During installation my brother accidentally restarted computer.
Then I went into terminal and I typed  again:
-> sudo apt-get install kubuntu-desktop
but got an error message and advise to run:
-> sudo dpkg --configure -a
This gave me the following output:

Setting up ttf-arphic-ukai (0.1.20060928-2.2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing ttf-arphic-ukai (--configure):
 subprocess post-installation script returned error exit status 1
Setting up kdm (4:3.5.8-0ubuntu2.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing kdm (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-arphic-ukai
 kdm

What can I do?

---

