---
title: "formatting external drive"
date: 2013-10-18
forum: Desktop Environments
---

### Post by richprim on 2013-10-18
When I format (using gparted) a external drive to say ext2 it always had "root" privileges so I have to log off, restart the computer and log in as root to change the permissions.

What am i doing wrong. Ubuntu 13.10.

Rich Prim

---

### Post by DuckHook on 2013-10-19
1. If you activated your root account in Ubuntu, you just circumvented one of Ubuntu's security measures. Root actions should always be run from your own unprivileged account using *sudo*, which only temporarily elevates you to root privilege for the purpose of that specific task. Using *sudo*, it is never necessary to log into a root account.
2. Nothing wrong with a drive being owned by root--your HDD is owned by root, but with permissions to allow you (when you are running your unprivileged user account) to access it.
3. If you wish to change ownership of the USB to your own unprivileged user, then after formatting your drive with gparted, you do:```
sudo chown -R your_name:your_name /media/"name_of_USB"
```...which will change the owner and group of the USB stick along with all existing directories and folders to you. However, this could prevent other users from accessing this media depending on the permissions you set.
4. Therefore, you can leave the ownership as root, but change permissions with```
sudo chmod -R 666 /media/"<name_of_USB>"
```...the -R flag will recurse through all directories in the USB stick to apply the same permissions to all directories and files you may have already created. This will allow universal read and write access to the USB stick, but not execute privileges.

You really should read [this]("https://help.ubuntu.com/community/RootSudo") and [this]("https://help.ubuntu.com/community/FilePermissions") to educate yourself on proper security measures and the concepts of ownership and permissions in Ubuntu.

---

### Post by richprim on 2013-10-19
Thank you for the excellent reply.
Too bad gparted doesn't have an option to change permissions, would be a great addition.
I did read the two "this" links.
Rich Prim near Philadelphia Pennsylvania USA

Ham operator WA3IWT

---

