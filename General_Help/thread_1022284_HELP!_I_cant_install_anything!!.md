---
title: "HELP! I cant install anything!!"
date: 2008-12-26
forum: General Help
---

### Post by dragos240 on 2008-12-26
Ok i'm trying to install something when this pops up:

```

user@ubuntu:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
user@ubuntu:~$ sudo apt-get install ndiswrapper-common
[sudo] password for user: 
Reading package lists... Error!
E: Could not open file /var/cache/apt/pkgcache.bin - open (116 Stale NFS file handle)
E: Failed to truncate file - ftruncate (9 Bad file descriptor)
E: The package lists or status file could not be parsed or opened.
user@ubuntu:~$ 

```I am completely out of space in my /tmp folder, although there is nothing inside, please help! Also i need something to clear my tmp, like tmpcheck, but i cant install that because of this problem.

---

