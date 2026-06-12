---
title: "Simple Automount NTFS with 3G when booting Ubuntu"
date: 2009-05-30
forum: General Help
---

### Post by Data-Base on 2009-05-30
Hello,

I just installed Ubuntu on my Home Server replacing Windows 2008 server, I have an issue with NTFS Partitions!?!

I saw few posts trying to cover this issue, but I could not get any useful solution!

sorry if this was already solved, but I was searching the forum and Google with no luck!

now here we go

I like to have the right line in **fstab** to mount NTFS partitions using 3G

when I run the command **mount** , I get this
> /dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro)
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
/dev/sda2 on /home type ext4 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/KingSam/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=KingSam)
/dev/sdb7 on /media/Music type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb2 on /media/KingSam type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb5 on /media/Programs type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb6 on /media/Video type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb8 on /media/Personal type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

how I can use the line **/dev/sdb8 on /media/Personal type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)** from the **mount** command output in **fstab **?

thank you

---

### Post by Data-Base on 2009-05-31
Solved!

found handy info

[http://www.debrass.net/2009/05/23/ubuntu-ntfs-support-ntfs-3g/](http://www.debrass.net/2009/05/23/ubuntu-ntfs-support-ntfs-3g/)
[http://ubuntuforums.org/showthread.php?t=685880](http://ubuntuforums.org/showthread.php?t=685880)

specially
[QUOTE="danwood76"]In gutsy **there is no difference between ntfs and ntfs-3g**.
Ntfs is just an alias for ntfs-3g.[/QUOTE]

Thanks!

---

