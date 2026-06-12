---
title: "Mounted NTFS Partition No read Just write"
date: 2009-01-04
forum: General Help
---

### Post by livet0ski on 2009-01-04
Hey,
I've got a bit of a problem with one of my NTFS partitions. I can browse around the directories fine but when I try to read a file off the disk I get permission denied. I've chmod'ed everything I can to 777 but when I do an ls -la for a file that I want to copy off the disk is get 
-rwxrwxrwx 1 root root ...

There is no "d" at the beginning which I believe means I cannot read it. I can write new files to the disk from Ubuntu. This partition was used before by both XP and then Vista so hopefully they didn't set any silly file attributes that is preventing me from getting this information off the disk. Anyone have any suggestions about what to do so I can get my data?
Thanks,
Pat

---

### Post by HermanAB on 2009-01-04
Look at how it was mounted and if necessary change /etc/fstab.

This will show you what is wrong:
$ sudo mount

Cheers,

Herman

---

### Post by livet0ski on 2009-01-04
hmm... ok I'm not that familiar with fstab, other than that i know it is used to auto mount at boot. Here is the output from sudo mount. See the problem? The hard drive I'm trying to mount is the dev/sda5.
Thanks for the quick response btw.

```
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/dev/sdb7 on /boot type ext3 (rw,relatime)
/dev/sdb5 on /media/MiSc type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /media/MuSiC type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/pat/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=pat)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=pat)
/dev/scd1 on /media/cdrom1 type iso9660 (ro,nosuid,nodev,utf8,user=pat)

```

---

### Post by mc4man on 2009-01-04
> There is no "d" at the beginning which I believe means I cannot read it
A d means directory, overall your permissions are correct as evidenced by being able to write to the volume

While I know it's possible for xp pro and vista to mark files as 'read only' that carries over to linux, I never seen where they could lock the files totally (except in vista -> security, but those permissions aren't enforced in linux. (to the extent I know

Do you see a X on the unreadable files or is it they just don't open? (with error message

If you still have windows I'd try running a chkdsk on the partition.

---

### Post by livet0ski on 2009-01-04
> Do you see a X on the unreadable files or is it they just don't open?
No there is no X on any of the files or folders. When I try to do just about anything to any file it says, "Error opening file: Permission denied"

> If you still have windows I'd try running a chkdsk on the partition.
I actually still had an XP cd lying around and booted off that into the recovery console and did a chkdsk. It found a bunch of errors the first time and took a while to fix them. I ran it again just to make sure and there were no errors. I still have the same problem with reading data. I'm not sure where to go from here.

---

### Post by livet0ski on 2009-01-06
anyone? bump.

---

