---
title: "Encrypted home-folder problem"
date: 2010-01-16
forum: Desktop Environments
---

### Post by new_tolinux on 2010-01-16
Hi,

I have Ubuntu 9.04 x64 running (although the problem was also there in 9.04 x86).
During the installation I choose to encrypt the home-folder.

Yet every time I am logged in (and the screen is not locked) it happens that it dismounts the folder and I can only get it back by going to the terminal typing ecryptfs-mount-private

Somehow it sometimes helps to keep a terminal-windows open in the ~ folder, but is there any normal way to prevent automatic dismounting of the private folder?
It should not be normal that when I'm logged in and programs are writing in the folder that it is dismounted by itself.

---

### Post by new_tolinux on 2010-01-20
Nobody out there who has an idea how to prevent this from happening during the time I'm logged in?

Already tried to set that the keyring must be rememberd until logout (so not the default 3 hours) but it did nothing.

---

### Post by new_tolinux on 2010-01-22
Ok... partly "solved" the problem.
I created another "Admin" user, copied all the important stuff out of my home-directory, then after a reboot I deleted the first user, it's group and it's home-folder.
After that I did apt-get remove ecryptfs-utils

Then created a new user with the same name, home-folder and ID (1000) as the deleted user and rebooted again.
Logged in as the first user, copied the stuff back and deleted the temporary user.

Seems that the problem is solved this way for now, but.... a real solution would still be apreciated.

---

### Post by new_tolinux on 2010-06-03
As I decided to use LVM without encrypting the home-folder after  installing 9.10, I won't put any more effort in solving this problem.  Therefore I'll marked it as solved.

---

