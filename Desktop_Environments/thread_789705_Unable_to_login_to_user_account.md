---
title: "Unable to login to user account"
date: 2008-05-10
forum: Desktop Environments
---

### Post by ballem on 2008-05-10
Hi all. I have a dual boot machine running Hardy KDE4 and Gutsy Gnome each in a separate partition with shared home and boot partitions. Problem is I have managed to screw up something in my home folder so that I cannot now login to my user account in Gutsy, I just get a beep after the password. I can login to Gutsy as root and can also login to my identical user account under Hardy which uses the same home folder. My user and group ID's and password are the same for both Hardy and Gutsy. Any helpful suggestions appreciated.

Mike

---

### Post by tamoneya on 2008-05-10
you probably changed the ownership of your home folder.  What is the output  ```
ls -la /home
```Also you could try setting your password again with```
sudo passwd your_username
```

---

### Post by ballem on 2008-05-11
> **tamoneya said:**
> you probably changed the ownership of your home folder.  What is the output  ```
ls -la /home
```Also you could try setting your password again with```
sudo passwd your_username
```
here is the output to the ls command:

total 48
drwxrwxrwx  6 root root  4096 2008-05-10 10:45 .
drwxrwxrwx 23 root root  4096 2008-05-09 21:58 ..
lrwxrwxrwx  1 root root    44 2007-06-20 23:15 .directory -> /etc/kubuntu-default-settings/directory-home
drwx------  2 root root 16384 2007-06-19 01:55 lost+found
drwxr-xr-x 72 mike mike  4096 2008-05-11 09:36 mike
drwxr-xr-x  2 root root  4096 2008-01-12 17:47 Recycled
drwx------  3 root root  4096 2008-05-07 22:00 .Trash-root

I had already tried resetting the passwd, doesn't make any difference. I suspect the problem is related to home folder permissions, I was messing about with them trying to get mediatomb to see my media folders, but have chown -R mike:mike mike and chmod -R 755 mike. Thanks for you help

---

