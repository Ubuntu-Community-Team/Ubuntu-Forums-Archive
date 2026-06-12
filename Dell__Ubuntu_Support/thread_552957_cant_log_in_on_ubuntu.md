---
title: "cant log in on ubuntu"
date: 2007-09-17
forum: Dell  Ubuntu Support
---

### Post by wardy on 2007-09-17
hi there.plese can you help .i can now not log in to ubuntu .the error message i am getting is" 60m could not write to your authorisation file.this could mean that you are out of disk space or that your home directory could not be opened for writing .in any case it is not possible to log in .contact admin. " do you no how i can resolve this  problem .?plese help as i cant do anything at moment .thanks alot.

---

### Post by ridgeland on 2007-09-30
When you boot does the GRUB menu offer options like a recovery mode? 
This mode will boot up to a terminal under control of root.  There you can
# cd /home
# ls -l
and see the list of users and the folder permissions.
Should be YourName preceeded by
drwxr-xr-x 25 YourName ....
Then to make sure all files there have the correct rights
# chmod -R 755 YourName
Then # exit
Then try logging in.
I just tried these steps on my second PC and it is still fine, it worked before, but still does after the chmod -R 755 too.

---

