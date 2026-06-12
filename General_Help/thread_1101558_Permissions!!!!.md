---
title: "Permissions!!!!"
date: 2009-03-20
forum: General Help
---

### Post by underdog512 on 2009-03-20
I have 2 user accounts set up on an Ubuntu 8.10 box.  My accout is able to access removable storage without any issue. When my wife tries to access a thumb drive or an SD card from her acct she gets a permissions error.

This is what I have tried so far.

I created a group called storage-media. I then launch nautilus as root using the command "sudo nautilus".  When I try to change the group rights under properties I get a permissions error! I am running Nautilus as ROOT!! how is that possible.


So then tried just running "sudo chmod -R 777 /media" then had her log out/in and still got same permissions error.

Is this a bug or am I doing somthing wrong? 

Either way, it should not be this difficult!

thanks in advance!

---

### Post by amendt on 2009-03-20
I am not sure all the groups the main user is apart of, but when using "sudo nautilus" you still have to be the main user to change permissions.

---

### Post by taurus on 2009-03-20
What filesystem is your thumbdrive. vfat or ntfs?  Try remounting it with umask so everyone can write to it.  NTFS and fat32/vfat don't play nice with permissions and ownerships.

```
sudo fdisk -l
df -h
```

---

### Post by jelle_ on 2009-03-20
go to system -> administration -> users and groups
press mid-below key, don't know enlish name, and enter your password.
go to properties -> user rights and put "can automatically use removable media" on. now she should be able to access the drive

---

### Post by underdog512 on 2009-03-21
> **jelle_ said:**
> go to system -> administration -> users and groups
press mid-below key, don't know enlish name, and enter your password.
go to properties -> user rights and put "can automatically use removable media" on. now she should be able to access the drive

I am not seeing that option under privileges.

---

