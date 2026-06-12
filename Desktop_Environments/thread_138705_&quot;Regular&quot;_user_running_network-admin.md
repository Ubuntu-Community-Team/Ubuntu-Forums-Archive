---
title: "&quot;Regular&quot; user running network-admin ?"
date: 2006-03-02
forum: Desktop Environments
---

### Post by knichel on 2006-03-02
I need to allow my students to run network-admin.  I tried to add a line to the /etc/sudoers file...

student ALL = NOPASSWD: /usr/bin/network-admin

This did not fix the problem. I am guessing that network-admin is running for them, but it requires access to something else that I am unaware of.  

I teach a cisco networking class and need the students to be able to change the network settings periodically.  The problem I am experiencing is this...

I have 2 wireless nic's in each PC. We have 1 wifi router for the internal network (the router rack for the students to configure) and 1 wifi router for the external network (internet access).  Ubuntu seems to keep setting the default gateway to the internal router.  THe only way I have been able to get the internet back on nthe PC is to delete the default gw ip address for the internal router.  I have not added the internal router as the default gw.  THe students do not have the ability to remove that route.  So, they cannot fix the problem.  

Any help would be appreciated...

Mike

---

### Post by tflanders on 2006-10-17
I have the same question. Does anyone have an answer?

---

