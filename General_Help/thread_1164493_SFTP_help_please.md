---
title: "SFTP help please"
date: 2009-05-19
forum: General Help
---

### Post by uge on 2009-05-19
Hi,

I'm a newbit with Linux.

My config is Ubuntu Server 64 bits, 8.04 LTS, and I use the Webmin GUI.

I want to allow SFTP connections.

When I create a user with /bin/bash shell, and setting their home folder to a FTP folder, I can successfully connect through SFTP but I don't end home in the home directory that I set (I end up in the root //), plus I can browse in a lot of place.

Here are my questions :
1) Is it possible to allow SFTP connection, without giving SSH access ?
2) How can I make it so when they log in, they end up in a specific directory ?
3) How can I "jail" them to their home directories and their subfolders ?


THANK YOU !):P

---

### Post by John Cheng on 2009-05-19
It is possible to allow secure FTP connection without going through SSH. Take a look at FTPS ([http://en.wikipedia.org/wiki/FTPS](http://en.wikipedia.org/wiki/FTPS)). I believe ProFTPD and VSFTPD both support FTPS. These two methods allows for the "jail" feature that you would like.

If you are using FTP over SSH, I do not believe it is easy to set a default "home" directory or jail them.

---

### Post by dmizer on 2009-05-19
> **John Cheng said:**
> It is possible to allow secure FTP connection without going through SSH. Take a look at FTPS ([http://en.wikipedia.org/wiki/FTPS](http://en.wikipedia.org/wiki/FTPS)). I believe ProFTPD and VSFTPD both support FTPS. These two methods allows for the "jail" feature that you would like.

If you are using FTP over SSH, I do not believe it is easy to set a default "home" directory or jail them.

For more information about the above and for a detailed howto, see the third link in my sig.

---

### Post by uge on 2009-05-20
ok then thanks !

---

### Post by dmizer on 2009-05-20
I suggest that you post the above in the tutorial thread. That way the maintainer of the tutorial can address your problem. Since I rely on SSH for my remote file connections, I really don't have a lot of experince with ftps and wouldn't know how to troubleshoot your problem.

---

### Post by uge on 2009-05-21
Whole new approach : got rid of ProFTPD completely and started up clean with MySecureShell.

Had to recompile it because it didn't fit my 64 bit architecture but other than that, it really really rocks !

I recommend it to everyone : easy set-up and ultra-secure

---

