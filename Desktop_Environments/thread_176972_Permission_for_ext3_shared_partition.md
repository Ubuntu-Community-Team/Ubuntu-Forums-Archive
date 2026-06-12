---
title: "Permission for ext3 shared partition"
date: 2006-05-15
forum: Desktop Environments
---

### Post by kmoz on 2006-05-15
Hi all,

I'm in the process of setting up a Breezy file/print server.  I've mapped a partition to /home/common and would like this to be readable/writeable by all members of the 'users' group.  However, I've tried adding 'guid=0100', and/or 'user' option to the fstab without much luck.  I did a chown 'users' on the folder and chmod 777, which allows anyone to write files.

However, if one member creates a folder, another member of the users group CAN NOT delete that folder.  How do I make a universal shared ext3 folder?

Thanks,

kmoz

---

