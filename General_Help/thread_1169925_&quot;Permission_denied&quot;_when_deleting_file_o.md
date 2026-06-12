---
title: "&quot;Permission denied&quot; when deleting file on external hdd"
date: 2009-05-25
forum: General Help
---

### Post by bcoffield on 2009-05-25
Hi,

I'm using 9.04 and when I try to delete anything on my external hard drive through nautilus I get a permission denied error.  I haven't made any changes that I can think of that might be causing this...  Any suggestions?  Thanks in advance!

Brad

---

### Post by taurus on 2009-05-25
Is it ntfs or fat32/vfat filesystem?  Try running nautilus with root privilege.

Applications -> Accessories -> Terminal
```
gksudo nautilus
```

---

### Post by bcoffield on 2009-05-25
Thanks for the quick and useful reply.

gksudo totally worked, thanks.

The filesystem is listed as msdos...Is that weird (lol)?

---

### Post by albinootje on 2009-05-25
> **bcoffield said:**
>  I'm using 9.04 and when I try to delete anything on my external hard drive through nautilus I get a permission denied error. 

Can you post the output of :
```

mount
cat /etc/fstab

```
I think it makes sense to find a permanent solution for this, by adjusting the mount options, so that permission problems like this will be avoided.

---

### Post by bcoffield on 2009-05-25
mount =
/dev/sda5 on / type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sdb1 on /media/sdb1 type vfat (rw,noexec,nosuid,nodev)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/brad/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=brad)




cat /etc/fstab =

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# / was on /dev/sda5 during installation
UUID=05c0da43-cbd3-4e50-8f52-e282e1f7a8ef  /              ext4         relatime,errors=remount-ro  0  1  
# swap was on /dev/sda3 during installation
UUID=357c7ff7-081f-49d1-b777-e7f26bd2fb97  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sdb1                                  /media/sdb1    vfat         user                        0  0  
brad@brad-laptop:~$ 





The external hd is sdb1...maybe that is obvious....

I see now that its listed as vfat... I got "msdos" from when I right clicked on it in nautilus and selected properties.

Thanks for the help!

---

### Post by taurus on 2009-05-25
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and modify the last entry to look like this.

```
/dev/sdb1   /media/sdb1   vfat  iocharset=utf8,umask=000  0  0
```
Save it and reboot.  You now should be able to write to /media/sdb1 without using sudo/gksudo.

---

### Post by bcoffield on 2009-05-25
Thanks, that worked.  Whatever it was :)

---

### Post by 007casper on 2009-06-28
I am trying to grsync my whole system to an external hard drive and I am getting permission errors. How can I fix this problem?

would taurus' command apply in my case?  I dont know what is wrong.  I also tried
> sudo chown -R $USERNAME. /media/disk

here is what the terminal shows for mount, and cat /etc/fstab

> ross@non:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-13-server/volatile type tmpfs (rw,mode=755)
/dev/sda2 on /home type ext3 (rw,relatime,errors=remount-ro,usrquota,grpquota)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/ross/.Private on /home/ross/Private type ecryptfs (ecryptfs_sig=91d4066870453544,ecryptfs_cipher=aes,ecryptfs_key_bytes=16)
gvfs-fuse-daemon on /home/ross/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ross)
/dev/sdb5 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/Local Disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
ross@non:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ddf6060c-f6ad-4964-b5b9-d5bdd2cc0dd5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=97be5e68-0421-4aaf-99fb-1a89e6b8b461 /home           ext3    relatime,errors=remount-ro,usrquota,grpquota 0       2
# /dev/sda3
UUID=5577fac6-71bf-4757-917f-3ebcb6149504 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
ross@non:~$ 


and here is the partial errors...

> rsync: opendir "/etc/chatscripts" failed: Permission denied (13)
rsync: opendir "/etc/cups/ssl" failed: Permission denied (13)
rsync: opendir "/etc/ppp/peers" failed: Permission denied (13)
rsync: opendir "/etc/ssl/private" failed: Permission denied (13)
rsync: opendir "/home/lost+found" failed: Permission denied (13)
rsync: opendir "/lost+found" failed: Permission denied (13)

I cant attach the text file because of the file size.

---

### Post by albinootje on 2009-06-28
First of all you better ommit /proc in your backups, /proc is a "special mirror" of the Linux kernel, and does not contain real files.

Second of all the permission errors (about /etc and /var/spool/postfix) make sense since you probably run grsync as normal user.

P.s. can you please shorten that long list, or put it there as a txt file attachment ? That would improve reading this page for everyone else.

---

### Post by 007casper on 2009-06-28
do I have to run grsync as root  ???

---

### Post by albinootje on 2009-06-29
> **007casper said:**
> do I have to run grsync as root  ???

If you want to make a copy of *all* of your files and directories in / ... then you should use sudo indeed.

---

