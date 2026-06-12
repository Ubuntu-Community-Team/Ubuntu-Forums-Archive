---
title: "Remote working from ubuntu-&gt;ubuntu"
date: 2005-04-23
forum: Desktop Environments
---

### Post by fipeso on 2005-04-23
Hi,
Im new to Linux.

I have installed 2 ubuntu PC, my client and server.

Now what is my options to remotely work on the server from my client?

---

### Post by Leif on 2005-04-23
I use nxclient, which is available from the backports, I think. See:

[http://ubuntuforums.org/showthread.php?t=15592&highlight=freenx](http://ubuntuforums.org/showthread.php?t=15592&highlight=freenx)
[http://ubuntuforums.org/showthread.php?t=1968&highlight=nxclient](http://ubuntuforums.org/showthread.php?t=1968&highlight=nxclient)

Otherwise, there's always vnc.

---

### Post by alastair on 2005-04-23
Install an ssh server (openssh-server) on the server, then on the client :

ssh <server>

---

### Post by fipeso on 2005-04-23
Thank you,

I did get the ssh, and its working  \\:D/ 

At first, I also got "Ubuntus own RemoteDesktop" to work, so I could use VNC viewer from the Desktop, but after I rebooted the server, that stoped working  ](*,) 
("Only thing" I had changed before boot was setting default depth to 8 in /etc/X11/xorg.conf)

I try to get that FreeNX working later :)

---

