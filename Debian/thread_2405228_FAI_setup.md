---
title: "FAI setup"
date: 2018-11-03
forum: Debian
---

### Post by child on 2018-11-03
I'm trying to set up my FAI server, but after reading the documentation several times i'm still stuck with a couple of questions. I have a working NFS and PXE setup, on top of which i want t o get FAI running.

The FAI server itself is an armhf machine. The main goal would be to install on x64 and x86 system. How does FAI support this? The documents suggest i only need to download some basefiles to my config folder. Some older tutorials, however, suggest multiplying  the configuration in '/etc/fai' per architecture. What i can see  from running the 'fai-setup' is that the nfsroot being created has only native armhf packages.

Another thing i can't get right is if and how fai generates the correct configuration for PXE booting. I've toyed around with it for a while, and while 'fai-chboot' generates the config file, i don't know what would generate the kernel that will boot on the clients. Even though i have basefiles downloaded in the correct folder, they are not extracted or used in any way.

Thanks for any clues!

---

### Post by oldos2er on 2018-11-03
Which version of Debian?

---

### Post by child on 2018-11-03
I am trying right now to install the current stable release, and if that succeeds, move onto the testing release. (as afaik testing and sid is unsupported by FAI)

---

