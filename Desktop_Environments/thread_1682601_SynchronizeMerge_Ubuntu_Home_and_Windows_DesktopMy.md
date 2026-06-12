---
title: "Synchronize/Merge Ubuntu Home and Windows Desktop/My Documents"
date: 2011-02-06
forum: Desktop Environments
---

### Post by srdjo on 2011-02-06
I have a simple problem but don't have a simple enough solution.

I have 2 machines, 1 Ubuntu 10.10 with LTSP installed on it that works great and 1 Windows 2003 Server where I have Terminal server running.

I also have DLink DNS-232 NAS where I do regular backups. Now here is the problem.

I would like to transfer Ubuntu's users Home folder and Windows User folder to my DLink NAS and use it from there. Or at least find the way to link my home folders to NAS so all the files stay on one place so that users can use it from both servers without running any sync software or waiting for files to sync.

---

### Post by Krytarik on 2011-02-06
Then, as you said, you could simply symlink the users home directories, or -more elegant- set their real (new) locations in "System -> Administration -> Users and Groups -> Advanced Settings -> Advanced".

In either case, you have to copy the directories to their new locations before of course.

Greetings.

---

### Post by srdjo on 2011-02-06
How to symlink home to network share ?

Do I have to mount it on boot first ? How to do that ?

---

### Post by Krytarik on 2011-02-06
As I said, I'd prefer the "settings way".

Honestly, I don't know anything about restrictions on network storage, but if it is mounted to a mount point, and I will safely assume that, you can symlink to them like to any other location. For example, I symlinked some files/dirs in my home directory to another partition, it's even another filesystem (FAT32).

In either case, the "location" must be accessible before the respective user logs in, so automount on boot is generaly a good idea.;-)

---

