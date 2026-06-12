---
title: "&quot;The system administrator has disabled access. . ."
date: 2006-10-07
forum: Desktop Environments
---

### Post by StarsAndBars14 on 2006-10-07
to the system temporarily."

This is what I get in GDM, when I try to log in as any other user but the main account on my box.

Usermod doesn't work, deleting and adding users/groups doesn't work, and failsafe sessions don't work.  I've tried a console login and I'm met with "Permission denied."

How can I fix this?

---

### Post by StarsAndBars14 on 2006-10-07
OMG never mind. . .

pam_access.conf was set to disallow logins from anyone except those in my main user group.

Its fixed now. :embarrassed:

I feel like such an idiot. 
Someone please delete this thread.

---

### Post by meman63 on 2007-04-27
Okay,I'm a newbie.How did you fix this,please?

---

### Post by meman63 on 2007-04-27
Can someone please point me in the right direction to fix this?
I spent three days loading this box,just to get this crazy error.
I'm sure the fix is easy,judging by the previous poster.

Please help!!??

Thanks,Monica

---

### Post by Arthur Archnix on 2008-03-02
gksudo gedit /etc/security/access.conf

make sure down at the bottom, all the usernames you want to allow to log on are listed.

---

