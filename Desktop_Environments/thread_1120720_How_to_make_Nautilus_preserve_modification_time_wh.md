---
title: "How to make Nautilus preserve modification time while copying files?"
date: 2009-04-09
forum: Desktop Environments
---

### Post by vaibhav on 2009-04-09
How to make Nautilus preserve modification time while copying files? I'm using Hardy.

---

### Post by StuartN on 2009-04-09
Nautilus / cp should preserve date & time within a filing system and between most filing systems, but there is bug [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/315552](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/315552) that affects some combinations. If I copy files from my EXT3 home partition to an external SMB share then the files all end up with the date and time that the copy is made (according to the clock on the receiving system). This appears to be a deep-down bug because using cp at the command line, even with the --preserve option, has exactly the same problem.

The only method that reliably works for me is to send files across by rsync, after setting up the rsync permissions on the receiving system.

---

