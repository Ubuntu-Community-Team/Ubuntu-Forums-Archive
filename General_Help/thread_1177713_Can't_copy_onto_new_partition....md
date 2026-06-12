---
title: "Can't copy onto new partition...?"
date: 2009-06-03
forum: General Help
---

### Post by MimziM on 2009-06-03
I have formatted a new ext3 partition(sda2) and have written into
/etc/fstab  the following line:

/dev/sda2  /home/user/data  ext3  defaults  0  0 

so when i boot it is mounted and i can open and view it, but
i cannot copy anything into it???

---

### Post by SuperSonic4 on 2009-06-03
Perhaps it's because root owns the drive? If prefacing the copy command with sudo/launching a root file manager works then it's likely to be a permissions issue.

You could try chowning the drive to your user if it's a permissions thing

---

### Post by MimziM on 2009-06-03
If it was permissions I'm sure it would tell me. I'm using GUI because
it 200GB I want to transfer. i dont even have the option to paste

---

### Post by SuperSonic4 on 2009-06-03
What error message comes up when you try to copy? Are you sure it's not copying in a popup window that's hidden?

---

### Post by MimziM on 2009-06-03
like i say not even the  option to paste anything at all
definitely not copying in hidden window
partition was created at install but not used
i' just formatted it ext3 and written the mount line
should i maybe delete partition and create completely new one?

---

### Post by merlinus on 2009-06-03
You might try mounting the partition in /media/data, and then if need be change ownership via the chown command in a terminal or running nautilus as root.

---

### Post by MimziM on 2009-06-03
Thanks merlin
opening nautilus as root did it for me :-)

---

