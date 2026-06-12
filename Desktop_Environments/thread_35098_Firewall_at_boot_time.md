---
title: "Firewall at boot time"
date: 2005-05-17
forum: Desktop Environments
---

### Post by celinek on 2005-05-17
Hello,
I've installed Guarddog and I would like to load /etc/rc.firewall script at boot time. I used to work with Slackware and I know how to do that in that distro. But I don't know  how to do that in Kubuntu because I'm using it from just a few days. I'll appreciate your help. Thanks!

---

### Post by az on 2005-05-17
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=guarddog&version=hoary&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=guarddog&version=hoary&arch=i386)

etc/init.d/guarddog					    net/guarddog [universe]


Guarddog runs on boot.  It does so before the network is up.

---

