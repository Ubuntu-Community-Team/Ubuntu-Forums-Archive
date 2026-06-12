---
title: "How to remove all remnants for a deleted user?"
date: 2006-08-02
forum: Desktop Environments
---

### Post by aum11 on 2006-08-02
Some time ago I deleted a user from the system.  Now I find that there are still many files belonging to that user under that user's home which are locked or unaccessable to me.

How to delete them from the system now?

---

### Post by cantormath on 2006-08-02
> **aum11 said:**
> Some time ago I deleted a user from the system.  Now I find that there are still many files belonging to that user under that user's home which are locked or unaccessable to me.

How to delete them from the system now?

what files are you trying to delete?
/home/user?

if thats so
cd home
sudo rm -rf user/

make sure that if you are deleting the original user that you made when you installed ubuntu, that you add a new user to admin group, or you might have problems with the new user doing stuff.

---

### Post by aum11 on 2006-08-02
Thanks...worked perfectly!  And such a quick response.

---

### Post by der_joachim on 2006-08-02
From the manual page for userdel:

[quote=man:userdel]
-r     Files in the user’s home directory will be removed along with the home directory 
itself and the user’s mail spool. Files located in other file systems will have to be searched for and deleted manually.
[/quote]

One catch: you've already deletd your user, and I do not know whether this would work for an already deleted user.

---

### Post by Dubbayoo on 2006-08-02
find / -user skippylunchmeat -print | xargs rm

---

### Post by ardchoille on 2006-08-02
> **Dubbayoo said:**
> find / -user skippylunchmeat -print | xargs rm

Does this work for users who have already been deleted?

---

