---
title: "Remote Access?"
date: 2009-04-20
forum: General Help
---

### Post by XGhozt on 2009-04-20
I've been searching and reading up on remote access/desktop/logmein services with Ubuntu. And they're really is no easy solution. But, as redundant as this topic may be, I wanted to clarify a few things..

If VNC is the only solution, is it secure? And are there any good solutions to working with a dynamic IP address? [DynDNS]("http://www.dyndns.com/")?

Is it possible to shell into my desktop using PuTTY? What about running an FTP server?

One really nice solution I was able to easily get working, was [dropbox]("http://www.getdropbox.com/").

I found [this]("http://ubuntuforums.org/showthread.php?t=541656"), but it was posted 2 years ago. Is it still a possible solution?

Thanks. :rolleyes:

---

### Post by KhurramM on 2009-04-20
***Hi***

Dropbox is a good option, but its mainly for data sharing.

U must use ssh server with ssh client if u want remote access in cli only.

All the gui options including vnc are not that secured as ssh is.

Be it dynamic or static is upto your personal requirements.

U are trying to mess up too much. My advice, take one task at a time so that u can get results, rather obscurity.

U can shell into any PC, as long as port 22 is open and ssh server is running on the remote PC.

Never ran into an ftp server, guess some one might queu u to it.

Hope I clear myself.

***Adios***

---

### Post by uncle-c on 2009-04-20
In addition, if you are worried about security you can ssh your vnc session. Also if you are planning to use Putty to ssh into your linux box from an XP machine you can also use Putty's sister program , psftp, to securely ftp into your linux box. You do not need to have a ftp server running on your linux machine as everything is under control of your sshd server.

---

### Post by James_Lochhead on 2009-04-20
SSH is a good idea. Nautilus (GNOME) and Dolphin (KDE) both have inbuilt SFTP clients (you don't want FTP - it is an outdated security liability). You can then transfer files easily between servers and where you are. This, for me, is one of the best feature of Linux. 

I can connect and easily modify my web servers and home directory at uni as if there files were on my computer (except for the speed).

 An added benefit is that I can wget torrent files to my web servers and then download them via SFTP - since this is a secure protocol the uni cannot detect I am downloading the .torrent files (which it blocks).

---

### Post by XGhozt on 2009-04-21
Thanks for the feedback everyone. I'll check out SFTP.

---

### Post by XGhozt on 2009-04-23
Alright, so I got SSH working and FTP working. But only over my local network. I also managed to get my IP to be static, so I don't need any other services to connect in remotely. However, it's just timing out for me.

Is there something I have to do in order to allow outside connections to these services on my desktop?
And would this have anything to do with multiple computers on the same static IP?

---

