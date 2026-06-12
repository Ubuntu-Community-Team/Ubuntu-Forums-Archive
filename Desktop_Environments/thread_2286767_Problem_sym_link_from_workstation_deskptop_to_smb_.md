---
title: "Problem: sym link from workstation deskptop to smb share on remote machine"
date: 2015-07-14
forum: Desktop Environments
---

### Post by Dave_Mann on 2015-07-14
dave@MightyWurlitzer:~$ sudo mount -a
[sudo] password for dave: 
mount: mount point smb://misterfixit/z/Documents does not exist

Here is my fstab line:
/home/dave/Desktop smb://misterfixit/z/ bind defaults,bind 0 0

Is this a permissions problem on target and Windows machine source or have I got this all wrong?

---

