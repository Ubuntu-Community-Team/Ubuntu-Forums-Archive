---
title: "Has anyone gotten tftpd to run on ubuntu 6.06?"
date: 2006-07-28
forum: Desktop Environments
---

### Post by while on 2006-07-28
Ihave been trying for a couple days to get this to work and I am still unable to. Has anyone gotten this to work? 

Thanks 

William

---

### Post by endfx on 2006-07-28
Ya, I have it working.
What is the problem?

When you install tftpd you need to add the line:
tftp            dgram   udp     wait    nobody  /usr/sbin/tcpd  /usr/sbin/in.tftpd /tftpboot

to /etc/inetd.conf

and make sure you have the folder /tftpboot 
and chmod 777 /tftpboot

You also need to install the inetd to run -- I recommend installing the openbsd-inetd package.

Just ask again if you need some clarification on this.

---

