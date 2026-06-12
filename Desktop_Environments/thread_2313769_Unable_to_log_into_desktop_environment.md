---
title: "Unable to log into desktop environment"
date: 2016-02-15
forum: Desktop Environments
---

### Post by nnamdi3 on 2016-02-15
Hi guys,
I'm an intermediate user of Ubuntu. While I was trying to setup Hadoop as admin, I updated my ~/.profile in order to add java PATH variables, after logging out, I was unable to login with my password. The login screen has not complained of wrong password, but yet, I can't login.

---

### Post by newbie-user on 2016-02-15
By chance do you know what you edited in .profile? Did you make a backup of .profile? Do you have another admin account you can log in with?

---

### Post by deadflowr on 2016-02-16
From memory, the user's .profile file is sort of imported from the /etc/skel/.profile file.
So, perhaps, boot into recovery mode and copy the /etc/skel/.profile into you users' home page's ~/.profile.
As recovery mode runs as root and sets up read-only, you'll need to do two things,
First, reset it read/write:
```
mount -o remount,rw /
```
and second, since the recovery shell will be set as the root user, you'll need to copy to your user's full path.
Something like:
```
cp /etc/skel/.profile /home/your-user-name/.profile
```
also, change the ownership as it will have retained the root ownership, which does not help your user.
```
chown your-user-name:your-user-name /home/your-user-name/.profile
```
Hope it helps

---

### Post by nnamdi3 on 2016-02-16
Thanks deadflowr, Your understanding and explanation lead me straight to the solution. 

:KSI appreciate

---

