---
title: "How to enable ftpd?"
date: 2006-08-21
forum: Desktop Environments
---

### Post by glennr on 2006-08-21
In desktop dapper how does one enable ftpd?

I have installed it but I can't figure out how to start it, there's no /etc/init.d/ftpd and /usr/share/doc/ftpd doesn't have any instructions.

What I'm trying to do is to allow machines on my home LAN to get access to an apt-mirror that I have on this machine. I figured the easiest way would be use ftp, but maybe there's another way to do it?

Glenn

---

### Post by taurus on 2006-08-21
You need to install either vsftpd or proftpd if you want people to ftp to your machine!!!

---

### Post by linuchsan on 2006-08-21
Have you proftpd installed as well?

---

### Post by glennr on 2006-08-21
Thanks for the fast response. I didn't have either of those packages installed. I choose proftpd and now have it working.

Took me a while to figure out how to configure it to serve up my mirror though because the default anonymous config is to chroot into /home/ftp and symlinks outside the chroot don't work.

The configuration I needed is this:

#<Anonymous ~ftp>
<Anonymous /path/to/my/mirror>

---

### Post by taurus on 2006-08-21
Yes, you can make it behave to whatever you want in proftpd.conf.

---

