---
title: "SAMBA differences between Xubuntu and Mint"
date: 2014-08-20
forum: Desktop Environments
---

### Post by ChrisRChamberlain on 2014-08-20
Hi all

Have a box running Linux Mint 17.

Final line in /etc/fstab is```
UUID=b5170b63-e2c4-44e6-8904-0089f586f269 /home/chris/Drive_D ext4 defaults,noatime 0 2
```

This auto mounts second hard drive.

Final block in /etc/samba/smb.conf
```
[251 GB]
    path = /home/chris/Drive_D/
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
```

Similar setup in Xubuntu 14.04

No auto mount, drive detected and mounted

Final block in /etc/samba/smb.conf
```
[251 GB]
    path = /mnt/sdb1/
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
```

So the Mint box can access '251 GB' on the Xubuntu box, but the Xubuntu box cannot access '251 GB' on the Mint box.

Have tried alternative paths for the Mint box, such as /dev/sdb1, without success.

Suggestions please?

TIA

---

### Post by yancek on 2014-08-20
If the fstab entry you posted above is on Mint for the Xubuntu drive, what is in the fstab on Xubuntu for Mint?  If these drives are on the same computer and have Linux filesystems, I'm wondering why you are using samba?

---

### Post by ChrisRChamberlain on 2014-08-20
yancek

Thanks for your reply.

These are two different computers on the same network.

The network is comprised of a Ubuntu server. various Windows desktop boxes, a Xubuntu 14.04 desktop box, and a Mint 17 desktop box.

---

