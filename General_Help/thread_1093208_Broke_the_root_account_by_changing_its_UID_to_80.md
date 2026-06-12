---
title: "Broke the root account by changing its UID to 80"
date: 2009-03-11
forum: General Help
---

### Post by wersdaluv on 2009-03-11
I ran **usermod -u 80 root** for me to copy the UID of the root account of OS X. It broke sudo, hal, and many other things. I can't use the mouse or keyboard. I'm on the live cd now. Is there any way for me to revert the changes I made?

---

### Post by taurus on 2009-03-11
Do you know which partition / is on?  You need to mount that partition somewhere.  Then, edit both /etc/passwd & /etc/group and change the UID of root from 80 back to 0.

---

### Post by heindsight on 2009-03-11
> **taurus said:**
> Do you know which partition / is on?  You need to mount that partition somewhere.  Then, edit both /etc/passwd & /etc/group and change the UID of root from 80 back to 0.

I believe you'll have to edit /etc/shadow too.

---

### Post by wersdaluv on 2009-03-11
> **taurus said:**
> Do you know which partition / is on?  You need to mount that partition somewhere.  Then, edit both /etc/passwd & /etc/group and change the UID of root from 80 back to 0.
You just saved my life :)

@heindsight
All I had to edit was /etc/passwd then everything worked. Thanks anyway :D

---

