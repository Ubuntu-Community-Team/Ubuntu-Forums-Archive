---
title: "Unable to access location Samba Share in Ubuntu Desktop"
date: 2017-03-08
forum: Desktop Environments
---

### Post by slkamath on 2017-03-08
Hi All,

In one desktop Samba Share is not working.

I can able see the samba share but if i try to access it says

Unable to access location.
Failed to mount windows share: permission denied 

System Configuration: Ubuntu 12.04 LTS

I created the Samba Share in the External Hard Disk

If i run testparm -s command:

```
root@eouma:/home/chikkaiah# testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[backup]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[backup]
    comment = Backup-B25
    path = /media/Backup/backup
    force user = administrator
    read only = No
```

So please help me to solve this issue.

Thanks in advance.

Thanks & Regards
Lokesh Kamath

---

### Post by TheFu on 2017-03-08
Support for 12.04.5 ends in a month, so it is time to move to a newer release.   Other versions of 12.04 lost support years ago.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

I'm in the same boat. Here I come, 14.04.

---

### Post by slkamath on 2017-03-09
Thanks for your information. 

My problem is not solved.

If I do the samba share in OS Installed drive it's working fine. If i do the samba share in External Disk it's not working i am getting error 

Unable to access location.
Failed to mount windows share: permission denied

Samba share wont support on External Hard Drive? Samba Share support only on OS installed drive?

So please help me in this regard.

Lokesh Kamath

---

### Post by TheFu on 2017-03-09
I'm not a samba expert. It always works for me, even on external disks.

I do some basic things, always.
* always setup networking on all the machines so that every system can ping every other system by-name. They all get the same answer.
* always use Linux file systems, not vFAT/FAT32 or NTFS.
* always have local file permissions correct for every mounted file system. For non-Linux file system mounts, this seems to be commonly incorrect.
* always setup new samba users with passwords using the smbpasswd tool.

The workgroup and preferred master settings seem to be missing from your smb.conf.  Thanks for the testparm.

---

### Post by slkamath on 2017-03-14
Thanks for your information.

I will once again check the file system. I think i formatted the Hard Disk in FAT32. I will once again format the partition with ext2 / ext3 file type and check and after that will inform.

Lokesh Kamath

---

### Post by TheFu on 2017-03-14
**ext4** is probably what you want. Ext2/3 are lacking in different ways.

---

### Post by slkamath on 2017-03-17
> **TheFu said:**
> I'm not a samba expert. It always works for me, even on external disks.

I do some basic things, always.
* always setup networking on all the machines so that every system can ping every other system by-name. They all get the same answer.
* always use Linux file systems, not vFAT/FAT32 or NTFS.
* always have local file permissions correct for every mounted file system. For non-Linux file system mounts, this seems to be commonly incorrect.
* always setup new samba users with passwords using the smbpasswd tool.

The workgroup and preferred master settings seem to be missing from your smb.conf.  Thanks for the testparm.

Thanks a lot. It started working for me. 

May be file-system was in fat32, I changed it to ext4. After that it started working.

Once again thanks.

Lokesh Kamath

---

