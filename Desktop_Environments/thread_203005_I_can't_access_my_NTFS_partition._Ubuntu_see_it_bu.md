---
title: "I can't access my NTFS partition. Ubuntu see it but won't let me browse."
date: 2006-06-24
forum: Desktop Environments
---

### Post by braveerudite on 2006-06-24
I have a dual boot system with a total of 3 partitions.

Ubuntu 6.06
Windows XP
Logical Partition (For storage) NTFS

Ubuntu detects the partition but would not let me browse it. [-( 

This is what I see in the Disk Manager Options:
--------------------------------------------------
acces path is:  /tmp/disks-conf-sda5 (By default)
status: accessible (But it isn't really) :-k 

--------------------------------------------------

When I press the browse button I get this message:

"You do not have the permissions necessary to view the contents of "disks-conf-sda5".  ](*,) 


I do not want to store anything on the NTFS partition, I just want to acces my music and videos files from Ubuntu. #-o 

Please help thx.

---

### Post by Ramses de Norre on 2006-06-24
Whats in your fstab? There should be an option umask=0222 for the ntfs drive.

---

### Post by lazyd2 on 2006-06-24
[Info here.]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only")

>  How to mount Windows partitions (NTFS) on boot-up, and allow all users to read only 

    e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS) 
    Local mount folder: /media/windows 

```
sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
```

    * Append the following line at the end of file 

```
/dev/hda1    /media/windows ntfs  nls=utf8,umask=0222 0    0
```


---

### Post by braveerudite on 2006-06-24
Thx so much for your time but I found a much easy way to do this in 2 steps here:  [https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

Sorry for wasting your time.  :(

I wish they made this more simple in future Ubuntu releases.  

Something like going to Disk Maneger, type password, pressing enable and actually the enable button working.

Thx so much for you time.

---

