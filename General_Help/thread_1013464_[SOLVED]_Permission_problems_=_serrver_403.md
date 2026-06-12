---
title: "[SOLVED] Permission problems = serrver 403"
date: 2008-12-16
forum: General Help
---

### Post by dethredic on 2008-12-16
So, I was playing around with permissions/ ownerships on my webserver, and now I get a 403 whenever I try to load my site.

Here is what I have:

> 
phil@ubuntu:~$ sudo rlogin 192.168.1.137
root@192.168.1.137's password: 
Last login: Tue Dec 16 21:40:09 2008 from 192.168.1.107
Linux server.hatchseadgroup.com 2.6.22-15-server #1 SMP Wed Oct 22 00:24:38 GMT 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
root@server:~# cd /var/www
root@server:/var/www# ls -l
total 1600
-rwxrwxr-x 1 root server 814080 2008-09-26 23:35 cfd.fla
-rwxrwxr-x 1 root server 786929 2008-09-26 23:35 cfd.swf
drwxrwxr-x 2 root server   4096 2008-10-21 15:23 images
-rwxrwxr-x 1 root server   3331 2008-11-01 21:48 index.html
drwxrwxr-x 5 root server   4096 2008-12-16 20:47 private
drwxrwxr-x 5 root server   4096 2008-12-16 20:47 public
drwxrwxr-x 2 root server   4096 2008-03-14 20:41 Scripts
-rwxrwxr-x 1 root server   2459 2008-03-20 23:22 style.css
root@server:/var/www# chgrp root *
root@server:/var/www# ls -l
total 1600
-rwxrwxr-x 1 root root 814080 2008-09-26 23:35 cfd.fla
-rwxrwxr-x 1 root root 786929 2008-09-26 23:35 cfd.swf
drwxrwxr-x 2 root root   4096 2008-10-21 15:23 images
-rwxrwxr-x 1 root root   3331 2008-11-01 21:48 index.html
drwxrwxr-x 5 root root   4096 2008-12-16 20:47 private
drwxrwxr-x 5 root root   4096 2008-12-16 20:47 public
drwxrwxr-x 2 root root   4096 2008-03-14 20:41 Scripts
-rwxrwxr-x 1 root root   2459 2008-03-20 23:22 style.css
root@server:/var/www# chmod 775 *
root@server:/var/www# ls -l
total 1600
-rwxrwxr-x 1 root root 814080 2008-09-26 23:35 cfd.fla
-rwxrwxr-x 1 root root 786929 2008-09-26 23:35 cfd.swf
drwxrwxr-x 2 root root   4096 2008-10-21 15:23 images
-rwxrwxr-x 1 root root   3331 2008-11-01 21:48 index.html
drwxrwxr-x 5 root root   4096 2008-12-16 20:47 private
drwxrwxr-x 5 root root   4096 2008-12-16 20:47 public
drwxrwxr-x 2 root root   4096 2008-03-14 20:41 Scripts
-rwxrwxr-x 1 root root   2459 2008-03-20 23:22 style.css
root@server:/var/www# 



I wouldn't think the owner or the group would matter much. And I can set it to 777 permissions and I still get the error.

Any ideas?

---

### Post by taurus on 2008-12-16
Shouldn't /var/www be owned by www-data instead of root?

---

### Post by dethredic on 2008-12-16
ok I figured it out. Although the contense of the www folder had 775 permissions, the folder itself had 770. Changed that to 775 and things are back up and running.

---

