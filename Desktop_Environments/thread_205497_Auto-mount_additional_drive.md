---
title: "Auto-mount additional drive"
date: 2006-06-28
forum: Desktop Environments
---

### Post by mykrob on 2006-06-28
I have a new system running Kubuntu 6.06LTS. It has 2 200GB sata drives, the second one is formatted ext3 and labeled "Storage". During installation, i told the installer to mount that drive as /storage, but it is not mounting..

how can i get this drive to mount automatically?

the drive is sdb1, a single partition. It currently does not show in the fstab file.

Thanks,
-myk

---

### Post by ajgreeny on 2006-06-28
Add a line much like the following to your fstab file, but change the mount point to whatever directory you have available, or have made in /media

/dev/sdb1       /media/storage   ext3    defaults  0  1

You can then enter *sudo mount -a* in a terminal to mount it, and it will be automounted each time at startup after that.

---

### Post by mykrob on 2006-06-28
got it, thank you!

Now, how do i make this drive writeable by all users?

Thanks,
-myk

---

### Post by mykrob on 2006-06-28
nevermind

chmod 777 /storage

---

