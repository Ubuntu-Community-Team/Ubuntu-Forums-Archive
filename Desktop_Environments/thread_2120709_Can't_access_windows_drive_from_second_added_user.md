---
title: "Can't access windows drive from second added user"
date: 2013-02-27
forum: Desktop Environments
---

### Post by atti84it on 2013-02-27
Hi! I've done these steps

1. Install Ubuntu 12.10 quantal (dual boot) specifying mount point for windows partition "/media/win-c". I did it during installation.

Everything works fine with first user: I can access windows drive without any problem.

2. I added a user from default GUI system settings tool. The role was "administrator".

With this user I couldn't access the same drive for not having enough rights. I noticed this user was not member of plugdev group, and my /media/win-c is owned by root user and plugdev group. So:

3. I added the second user to plugdev group

but still I can't access the drive with second user. With root and first user there's no problem. Any idea?

---

### Post by gordintoronto on 2013-02-27
It's unusual to create a mount point for a Windows partition. Without it, you can run Nautilus, and the Windows partition will appear on the left side, as "320 GB Filesystem," for example. One click and you're there, with full privileges.

---

### Post by fdrake on 2013-02-27
> **atti84it said:**
> Hi! I've done these steps

1. Install Ubuntu 12.10 quantal (dual boot) specifying mount point for windows partition "/media/win-c". I did it during installation.

Everything works fine with first user: I can access windows drive without any problem.

2. I added a user from default GUI system settings tool. The role was "administrator".

With this user I couldn't access the same drive for not having enough rights. I noticed this user was not member of plugdev group, and my /media/win-c is owned by root user and plugdev group. So:

3. I added the second user to plugdev group

but still I can't access the drive with second user. With root and first user there's no problem. Any idea?
output:
```
less /etc/fstab
```

---

### Post by atti84it on 2013-03-01
Hi Thanks for your answers. Since in old versions you needed to mount the partition into fstab I was doing that. Yesterday **I commented out** the mount line in fstab and still have the problem.
My fstab is the following:

[FONT=courier new]UUID=4526486b-2beb-44fe-ae77-18c2a81f08ec /               ext4    errors=remount-ro 0       1
# /media/win-c was on /dev/sda1 during installation
#UUID=FE14F8E614F8A337 /media/win-c    ntfs    defaults,umask=007,gid=46 0       0 <=== this I commented
# swap was on /dev/sda2 during installation
UUID=814fff3b-ce68-4e9a-9c25-fd240f9d2284 none            swap    sw              0       0[/FONT]

From first user I can access everything. From second user I got the error "The location is not a folder", so I googled the error and I got to this: [http://askubuntu.com/questions/204119/mount-issue-in-ubuntu-12-10/204226#204226](http://askubuntu.com/questions/204119/mount-issue-in-ubuntu-12-10/204226#204226)

So** I chmodded**:

[FONT=courier new]sudo chmod 775 /media/firstuser[/FONT]/

and actually gained some rights (it was drwxr-x---+ before) and **now I get** "**Not enough rights**" **error**:

[FONT=courier new]ls -lh /media/firstuser/[FONT=arial] shows:[/FONT]

drwx------ 1 firstuser firstuser 8,0K feb 28 17:26 FE14F8E614F8A337[/FONT]

and no way to change it: I chmodded 775 on the folder FE... but it doesn't change.

---

