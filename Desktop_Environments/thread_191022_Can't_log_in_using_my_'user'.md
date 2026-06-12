---
title: "Can't log in using my 'user'"
date: 2006-06-07
forum: Desktop Environments
---

### Post by Mishal on 2006-06-07
The message says something like "GDM can't start because there is low disk space or the "home" directory cannot be written over". Basically, either I don't have space in the partition where ubuntu is installed or somehow my file permissions are messed up.

As for the second possibility, I logged in as root (yes, I can still do that!) and tried combinations of permissions for my home folder. But I just can't log in.

I will delete Breezy and install Dapper within a few days but I still want to log in to my Breezy install and do some last minute work.

So, please help.:)

---

### Post by adwait on 2006-06-07
Well login as root and use
```
df
```

That will tell you if your home partition is full, if it is you need to delete some files to make space.

---

### Post by aysiu on 2006-06-07
You may find *df -h* more "readable": ```
username@ubuntu:~$ **df**
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda7              9187068   2865912   5854472  33% /
varrun                  225648        60    225588   1% /var/run
varlock                 225648         4    225644   1% /var/lock
udev                    225648       140    225508   1% /dev
devshm                  225648         0    225648   0% /dev/shm
lrm                     225648     18856    206792   9% /lib/modules/2.6.15-23-386/volatile
/dev/hda5            128582144  46469588  76887256  38% /documents
username@ubuntu:~$ **df -h**
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda7             8.8G  2.8G  5.6G  33% /
varrun                221M   60K  221M   1% /var/run
varlock               221M  4.0K  221M   1% /var/lock
udev                  221M  140K  221M   1% /dev
devshm                221M     0  221M   0% /dev/shm
lrm                   221M   19M  202M   9% /lib/modules/2.6.15-23-386/volatile
/dev/hda5             123G   45G   74G  38% /documents
username@ubuntu:~$
```

---

### Post by Mishal on 2006-06-07
Thanks guys. I found out that the trash folder in my home directory was 3.4GB.
Deleted that and everything's fine.:)

---

