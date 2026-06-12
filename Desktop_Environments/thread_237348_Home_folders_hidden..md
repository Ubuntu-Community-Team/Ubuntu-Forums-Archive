---
title: "Home folders hidden."
date: 2006-08-16
forum: Desktop Environments
---

### Post by artinla on 2006-08-16
I have two drives with working Ubuntu loads on them.  If I install them both, I cannot see any files in the home folder of the one not booted from.  The files are there, I just can't see them.  I have tried starting nautilus with root priveledge, but still can't see the home folder contents.  Can I do something to fix that?

---

### Post by louis_nichols on 2006-08-16
Is it just the home folder that you can't see from the other install? Do you see all the others: bin, etc, usr, var, tmp, mnt etc. (no, etc is not a folder :) )? Did you successfully mount the partition?

---

### Post by hecato on 2006-08-16
Then you setup is some like???

> 
firstHD
/ (mount point of first partition [or whole disk] of first install)
secondHD
/ (mount point of second partition [or whole disk] of second install)
 
???

Perhaps you have more partitions... and you havent mounted the partition that contain the /home folder of the other HD... (perhaps, my guess)... that is you have more than 1 partition not like the anterior guess in the "quote".

---

### Post by artinla on 2006-08-16
Yes, I have two drives.  Both are one big partition and both contain fully working copies of Ubuntu.  One Hoary, one Dapper.

Just cannot see any files within the home folder of the non-booted drive.

Art

---

### Post by hecato on 2006-08-16
I normally can see the content of other partitions if I have installed another distro there...



What about a liveCD or run ubuntu in the live CD, and use gparted for see how is "watched" the diferent HDs.... ¿?¿?¿?

---

### Post by annda on 2006-08-16
have you tried logging in as root to see if the problem persists (and is not user-related)?

i remember reading that UID can be an issue when accessing "external" /home directories. maybe try to change your user id so that they match in both your installs.

this is only a guess because i have only one install and can't try it out.

---

