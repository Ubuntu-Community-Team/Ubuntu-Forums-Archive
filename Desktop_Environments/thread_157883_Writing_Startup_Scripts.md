---
title: "Writing Startup Scripts"
date: 2006-04-10
forum: Desktop Environments
---

### Post by hit3k on 2006-04-10
Hi, I'm writing a script for a friend who uses ubuntu and who wants to mount his windows partitions at startup how would i write this script and how would i add it to init.d?

---

### Post by incubus on 2006-04-10
But why would you write a script for that? Can't you (he/she) add an entry in /etc/fstab?
[https://wiki.ubuntu.com/MountNtfsOnBoot?highlight=%28fstab%29](https://wiki.ubuntu.com/MountNtfsOnBoot?highlight=%28fstab%29)

If for some reason you still want to write a script and use init.d, I'd suggest reading this:
$ man update-rc.d

incubus

PS: Here's some more:
[https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=%28fstab%29](https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=%28fstab%29)
[https://wiki.ubuntu.com/AutomaticallyMountPartitions?highlight=%28fstab%29](https://wiki.ubuntu.com/AutomaticallyMountPartitions?highlight=%28fstab%29)

---

### Post by webra on 2006-04-10
Look here:

[https://wiki.ubuntu.com/MountNtfsOnBoot?highlight=%28ntfs%29](https://wiki.ubuntu.com/MountNtfsOnBoot?highlight=%28ntfs%29)

EDIT: incubus,  you beat me to it !

WebRa

---

### Post by hit3k on 2006-04-10
Argh I completely and utterly forgot about fstab >.< no I'm doing most of his stuff for him for the first few days

---

