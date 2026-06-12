---
title: "Login problem"
date: 2006-09-23
forum: Desktop Environments
---

### Post by lalousis on 2006-09-23
Today I tried to logon to Ubuntu and I had a problem.
I insert the correct username and password, but it seems to login and logout instantly.
Only in safe terminal mode I can login, but I don't know what to do....

---

### Post by henriquemaia on 2006-09-23
Boot in recovery mode. Then, backup your failed username home directory in order to remove it. Then login again with that user.

You can do that by typing on a terminal:

```
mv /home/your_username_home/ /home/backup_your_username_home
```Then logout and login as the previously failed user. Probably that will do the trick. Later on, if everything is ok, you can recover the files from your previous home by accessing the backuped folder.

---

### Post by lalousis on 2006-09-25
Thanks man, that worked!!!

---

