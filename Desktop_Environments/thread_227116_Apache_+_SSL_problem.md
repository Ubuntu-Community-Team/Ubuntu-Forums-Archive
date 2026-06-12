---
title: "Apache + SSL problem"
date: 2006-08-01
forum: Desktop Environments
---

### Post by t800t8 on 2006-08-01
I'm trying to follow this HOWTO ([HOWTO - Apache2 + Subversion + SSL]("http://www.ubuntuforums.org/showthread.php?t=51753")) but when I try to add port 443 to ports.conf in Dapper Drake 6.06 by using

```
sudo echo "Listen 443" >> /etc/apache2/ports.conf
```

I've got a "Permission denied" message.

How can I fix it? Thanks a lot

---

### Post by t800t8 on 2006-08-01
Fixed it myself: Stop Apache first

---

### Post by t800t8 on 2006-08-01
I have another problem with Apache + SSL. I can configure Subversion + Apache + SSL, it works well. But I use SVNPath so it supports only one repository. I try to change SVNPath to SVNParentPath but have "403 Forbidden".

Can anybody help me to fix it? Thanks

---

### Post by t800t8 on 2006-08-01
You can see how I setup Apache + SSL + Subverion here: [ Subversion + Apache2 + SSL on Ubuntu in 10 steps]("http://t800t8.net.tf/2006/08/subversion-apache2-ssl-on-ubuntu-in-10.html")

---

### Post by killernurd on 2006-09-14
You'll need to check your SVN repo's permissions and make sure that the repo is www-data read/writable.

Also, you need to include 'SVNListParentPath on' in the DAV config so that the server lets users browse the svn repos.

---

