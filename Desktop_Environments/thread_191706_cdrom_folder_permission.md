---
title: "cdrom folder permission"
date: 2006-06-07
forum: Desktop Environments
---

### Post by miguelgomes79 on 2006-06-07
Im having problems reading some folders of my backup cdrom.
When i login on my primary account i have full access to my cdrom, and all subfolders.
When i login with a secondary user account i cant read some folders and subfolders of my cdrom.
I have this problem only on Dapper.
When i was on breezy, i could read all folders with several accounts.

How can i fix this?

---

### Post by murataht on 2006-06-08
i don't know exactly howto do it, but there are some hints.

1) check the permission of the folders that you can not access, using gnome graphical interface or "ls -l"; if the permission or owner is not correct then:

2) check the /etc/fstab file, there should be mounting options for cdrom. maybe you can alter the options to correct it. ("man mount" will show options for mounting)

good luck.

---

### Post by Sutekh on 2006-06-08
[quote=miguelgomes79]Im having problems reading some folders of my backup cdrom.
When i login on my primary account i have full access to my cdrom, and all subfolders.
When i login with a secondary user account i cant read some folders and subfolders of my cdrom.
I have this problem only on Dapper.
When i was on breezy, i could read all folders with several accounts.

How can i fix this?[/quote] Can you enter these commands?
```
groups <first username>
groups <second username>
``` Is the second user in the **cdrom** group?

If not, use
```
sudo adduser <second username> **cdrom**
``` to add them to it.  This should give them access. 

There may be other groups that need changing for other functions.

---

### Post by miguelgomes79 on 2006-06-08
i tried the groups command, and all gave me: adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin

 I tried the command sudo adduser <second username> cdrom , and it displays the message:  is already a member of `cdrom'

I think this is a security problem, the sudo command in breezy gave me more options than on dapper.

For example, on breezy i normally done AVG scans for virus, and AVG checked the roor folder, but on dapper AVG cant check root folder, only home folder.

I thing dapper have more restrictive rules than breezy.

---

