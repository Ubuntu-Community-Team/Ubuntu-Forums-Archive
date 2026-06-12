---
title: "Mount NTFS drive on Boot"
date: 2006-09-24
forum: Desktop Environments
---

### Post by quickq111 on 2006-09-24
For some reason all the external USB harddrives formatted to NTFS mount on Ubuntu, so I can view them. But, for some reason, my internal one won't and I'm forced to enter this in terminal every time:

sudo mount /dev/sda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

Is there any way Ubuntu can Mount this NTFS drive on boot so I don't need to constantly enter the above in Terminal?

Thanks

---

### Post by ogu on 2006-09-24
you can save that into a file say we call it "mount" and set the file to run at startup

(Preferences->sessions->Startup Programs)

:)

---

### Post by quickq111 on 2006-09-24
What do I save the file as?

---

### Post by CatKiller on 2006-09-25
> **quickq111 said:**
> For some reason all the external USB harddrives formatted to NTFS mount on Ubuntu, so I can view them. But, for some reason, my internal one won't and I'm forced to enter this in terminal every time:

sudo mount /dev/sda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

Is there any way Ubuntu can Mount this NTFS drive on boot so I don't need to constantly enter the above in Terminal?

Thanks

Put it in your /etc/fstab file: [the Unofficial Ubuntu Guide]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only") has details.

---

