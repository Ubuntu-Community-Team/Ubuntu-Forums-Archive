---
title: "Not enough permission"
date: 2009-01-11
forum: General Help
---

### Post by arthur2710 on 2009-01-11
I just reinstalled Ubuntu, I had server version with xbuntu GUI, now I have desktop Ubuntu. When I try to do something in my USB hard drives it tells me I dont have enough permission. So I changed the owner
arthur@arthur:~$ sudo chown -h arthur /media/MAX250
but it still does not let me do anything. So I changed the permissions. 

arthur@arthur:/media$ ls -l
total 16
lrwxrwxrwx  1 root   root    6 2009-01-10 16:44 cdrom -> cdrom0
drwxr-xr-x  2 root   root 4096 2009-01-10 16:44 cdrom0
drwxrwxrwx  7 arthur root 4096 2008-12-31 00:16 HD
drwxr-xr-x  8 arthur root 4096 2008-12-30 23:17 MAX250
drwxrwxrwx 10 arthur root 4096 2009-01-10 23:19 WD250
 

arthur@arthur:/media$ sudo chmod -R a+rwxrwxrwx MAX250

only if I set it to rwxrwxrwx then can I do something. If I take off the last one to rwxrwxr-x, I cant do anything. The last one is "other" but I am logged into the first account.

---

### Post by taurus on 2009-01-11
What filesystem is the partition/drive that mounted to /media/MAX250?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

