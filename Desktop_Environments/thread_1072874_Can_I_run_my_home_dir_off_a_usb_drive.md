---
title: "Can I run my home dir off a usb drive?"
date: 2009-02-17
forum: Desktop Environments
---

### Post by askvictor on 2009-02-17
I want to put my entire home drive on a usb stick to use between a few different computers. I know I could edit /etc/passwd to point the home dir to /media/MyDisk (or whatever). The problem I have is with permissions. I can format the disk to ext3, but the UID of my login is different between the machines. I guess I could mess around with groups and umask. Any other thoughts? Is this a bad idea? What sort of issues might I run into?

---

### Post by gorilla on 2009-02-18
It's not a good idea to share config files between different distributions or versions of distributions. Better let them systems keep their own home, and mount the usb drive into a folder under home.

---

### Post by askvictor on 2009-02-18
Some of the config files are what I need to transport. The distro and version will be the same on all machines; some applications will be installed on some machines but not others.

---

### Post by Reeman on 2009-02-18
> **askvictor said:**
> I want to put my entire home drive on a usb stick to use between a few different computers. I know I could edit /etc/passwd to point the home dir to /media/MyDisk (or whatever). The problem I have is with permissions. I can format the disk to ext3, but the UID of my login is different between the machines. I guess I could mess around with groups and umask. Any other thoughts? Is this a bad idea? What sort of issues might I run into?
In theory it could happen but /etc/fstab and passwords might be a nightmare. 

One thought you could just unhide all your desktop configuration files and saved stuff then copy them straight to a non-configured new user on the other installs. Then run as the user. You should be able to run the set of configuration files as what ever user. If you do not have some of the same software installed it should not matter...for example if you have a .googleearth folder in /home/whoever but no googleearth install it should not bork things up.

---

