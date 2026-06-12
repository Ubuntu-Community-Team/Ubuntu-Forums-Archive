---
title: "hostname change premanently"
date: 2010-02-19
forum: Desktop Environments
---

### Post by vksingh on 2010-02-19
Hi, 
 I tried to change my hostname by following command: 
 
$ hostname host_name 
 
But when I reboot my laptop , I lost it and got reset to previous one. 
 
Any body can help. 
 
Thanks, 
 
Vivek

---

### Post by Hero of Time on 2010-02-19
Never thought about the fact that it's an administrative task and thus needs to be run as root?
You can also edit /etc/hostname and /etc/hosts to change the hostname. It's best to become root before editing the files, as sudo might not like the change from one of the files.

---

