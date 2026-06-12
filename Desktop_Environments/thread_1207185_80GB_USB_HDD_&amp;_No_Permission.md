---
title: "80GB USB HDD &amp; No Permission"
date: 2009-07-07
forum: Desktop Environments
---

### Post by th1bill on 2009-07-07
I have an 80GB harddrive that I formatted with a Gparted Live CD to be ext3.  I purchased a USB case for external use and the drive mounts with no problem.  When I try to back up my home directory by dragging and dropping I am told I do not have root privilege and when I look at the permissions for the drive they are all grayed out. 

Help please.

---

### Post by snakeman21 on 2009-07-08
A single Terminal command should do the trick.  

```
sudo chown username /dev/sdb
```

replace "username" with your user name, and "/dev/sdb" with the actual mount point of the external drive.  The drive must be connected for this to work.  If you do not know the mount point of you drive, check gparted, it will tell you.

After running the command, you may have to disconnect and reconnect the drive.

Edit:  Just so you have a better understanding of what's going on, the command "chown" is short for "change owner", or "change ownership".

---

