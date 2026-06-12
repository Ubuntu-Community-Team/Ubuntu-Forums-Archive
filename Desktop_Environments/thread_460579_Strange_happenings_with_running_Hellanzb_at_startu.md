---
title: "Strange happenings with running Hellanzb at startup"
date: 2007-05-31
forum: Desktop Environments
---

### Post by icedfusion on 2007-05-31
Hi,

I have (for a while now) been running hellanzb for all my newsgroup needs and also its web interface hellahella.

My problem is that I have added both the 'startup commands' to the session manager so that both services run at startup, i.e.:

hellanzb.py 

and 
paster serve /etc/usr/hella.ini

My problem appears to be that both services are activated as I can see them in the process list but they do not actually do anything. 
I find that to get them to work, I first have to kill off the processes and then restart them manually using the exact same commands as provided in the session startup.

Does anyone have a clue what this could be or have another way to startup programs after/during login???

I have tried adding the same commands to the rc.local file - but the processes do not even start.

thanks

ice.

---

### Post by g8m on 2007-06-01
I dont know hella, I use klibido. 

Just some points to check.

If you start it manually, they are run under your account. 
If you start it with the bootscripts, they are run as root.

Could it be some configuration files that are not found as root. Or a permission issue.

Anyway, hunt for errors in logs.

---

