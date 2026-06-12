---
title: "chown problems"
date: 2006-09-10
forum: Desktop Environments
---

### Post by Kurt_Alan on 2006-09-10
**[SIZE="5"][/SIZE]**

I want to remove some SBackup folders from /var and /home   But ALL my directories are locked because I am not the owner.  The owner is "root."
I have tried man, info, two books and Internet and still fail.  The following have failed:

```

``` chown root /u 

```

``` chown -hR root /u  

```

``` sudo chown /home/kurt/backup

```

```  sudo chown kurt /

What am I missing and what should I do?

---

### Post by croak77 on 2006-09-10
You should user a owner and a group like chown kurt:kurt /home/kurt/backup

Be careful though esp. with chown -R. If you do chown -R on / it could will change everything on your system folders and files. 

If you want to delete something who's owner is root. Try running your file-manager as root. Like gksudo nautilus.  Or sudo rm -r /home/kurt/backup. But again be very, very , very carefull using sudo rm -r. You could delete alot more then you want. I would use sudo rm -ir. That way it will ask before deleting.

---

