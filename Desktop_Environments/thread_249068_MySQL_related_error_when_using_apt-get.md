---
title: "MySQL related error when using apt-get"
date: 2006-09-02
forum: Desktop Environments
---

### Post by nolanjurgens on 2006-09-02
I'm trying to install Bacula and when I go to install the bacula-director-mysql package I get the following:

```
$ sudo apt-get install bacula-director-mysql
Reading package lists... Done
Building dependency tree... Done
bacula-director-mysql is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up bacula-director-mysql (1.36.3-2ubuntu2) ...
Checking DB connectivity...Ok.
Creating Catalog "bacula" ...Ok.
Creating tables ...Ok.
**ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)**
dpkg: error processing bacula-director-mysql (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bacula-director-mysql
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I'm assuming the bolded line is related to MySQL. I'm pretty new to SQL so I've been using phpMyAdmin instead of the command line. I created a password for the root account, but I'm never prompted for it during the install. I have another program using the database under a different user and it runs fine so I figure MySQL must be up and running okay. I saw some other threads with people having this error show up when trying to set their passwords for the first time, but none where it happened while using apt-get.

Does the bolded error message mean that it's not even trying to send a password? Either way, if anybody has some ideas on how to fix this I'd appreciate it.

---

### Post by Uluen on 2006-09-02
[QUOTE=nolanjurgens]
**ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)**Does the bolded error message mean that it's not even trying to send a password?[/QUOTE]Looks like it.

It's a long shot but maybe you can remove the root password just for this? Not pretty but it might work :)

---

