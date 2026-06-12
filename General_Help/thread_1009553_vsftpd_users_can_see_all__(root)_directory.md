---
title: "vsftpd users can see all / (root) directory"
date: 2008-12-12
forum: General Help
---

### Post by gotix on 2008-12-12
I use Ubuntu server edition 8.0.4.1
When I connect to the server with a regular user (myuser for example), i can see /home/myuser (default home). But the problem is that I can see the content of /home directory, then I can go up and see the content of root directory ("/"). And from there, I can inspect all the file hierarchy. How can I stop that, and prevent a user to see the content of other directories?
thanks

---

### Post by spiderbatdad on 2008-12-12
this will depend on file permissions. obviously your account is the admin account, and will of course be able to view all files. Other accounts will be able to view some system files, not all. If you want a private /home, you will need to set permissions such as 700 for directories and 600 for files.
Other options might include setting up a chroot, which can be tricky to do well. [http://undeadly.org/cgi?action=article&sid=20080220110039](http://undeadly.org/cgi?action=article&sid=20080220110039)
Some limits can be set in sshd_config.

---

### Post by gotix on 2008-12-12
Thanks, I enabled "chroot_local_user=YES" in /etc/vsftpd.conf, seems everything is fine now.
Is there any security risk by using this, by the way?

---

