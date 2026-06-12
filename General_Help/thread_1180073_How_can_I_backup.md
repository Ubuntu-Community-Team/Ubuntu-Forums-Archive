---
title: "How can I backup?"
date: 2009-06-06
forum: General Help
---

### Post by letmekilluplz on 2009-06-06
I want to backup so that I cant separate my /home and / partitions. Does anyone know a good way to backup just my /home so that I don't lose all my settings and programs?

---

### Post by blueridgedog on 2009-06-06
What are your options to backup to?  Do you have a DVD burner, CD writer, Flash drive (USB thumb drive), external hard drive?  

Tell me the media you have to backup to and I will suggest a method of using it efficiently.  I recommend you get a 4 gig USB flash drive and use it, unless you have a massive collection of images and songs.  In that case, I suggest you use an external hard drive.

---

### Post by letmekilluplz on 2009-06-06
I have a 16GB flash drive and a 250GB external drive take you pick. ;) I don't care so whichever you think will be best. All my songs, pics, etc are on the external so my install isn't that big.

EDIT - According to disk usage analyzer my /home is only 334.9MB so it will easily fit

---

### Post by blueridgedog on 2009-06-06
Well, if you plug in your USB flash drive and note where it mounts with the command 
```

mount
```

You can then backup your home directory with the command:
```

rsync -av /home/ /media/yourflashdrive --delete
```

You will replace /media/yourflashdrive with the location that your drive mounts to.  You can omit the --delete the first time, but when you run it subsequent times, it will delete files from the backup that have been deleted on the source (your home directory).

Just to be safe, you can also make a directory on your external drive called backups, and then put a copy there as well.

```
rsync -av /home/ /mnt/locationofexternaldrive/backups --delete
```

If you are not comfortable with looking up the mount locations of these drives, you can post the output of mount and I will help you.

---

### Post by letmekilluplz on 2009-06-06
```
sean@sean-desktop:~$ rsync -av /home/ /media/dev/sdc1
sending incremental file list
rsync: writefd_unbuffered failed to write 4 bytes [sender]: Broken pipe (32)
rsync: mkdir "/media/dev/sdc1" failed: No such file or directory (2)
rsync error: error in file IO (code 11) at main.c(594) [receiver=3.0.5]
rsync: connection unexpectedly closed (9 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(600) [sender=3.0.5]
```

Here is my mount
```
sean@sean-desktop:~$ mount
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
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/sean/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sean)
/dev/sr0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=sean)
/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sde1 on /media/FreeAgent Drive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
```


Sorry about the long reply I was away

---

### Post by blueridgedog on 2009-06-06
It looks like the usb key is:
```

/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
```

It is mounted on /media/disk, so the command you want would be:

```
rsync -av /home/ /media/disk
```

You may want to sudo it, if there are other users in /home/

---

### Post by letmekilluplz on 2009-06-06
OK I did that and it backed up ok it seems but now when I log in I get a > ....user's home/.drmc is being ignored.......

I can't have a background or themes or anything any help?

---

### Post by colau on 2009-06-06
> **letmekilluplz said:**
> OK I did that and it backed up ok it seems but now when I log in I get a 

I can't have a background or themes or anything any help?
You could also use grsync
```

aptitude install grsync

```

---

### Post by letmekilluplz on 2009-06-06
His backup solution is fine I just need a solution for the error mentioned earlier

---

### Post by blueridgedog on 2009-06-07
> **letmekilluplz said:**
> OK I did that and it backed up ok it seems but now when I log in I get a 

I can't have a background or themes or anything any help?

This thread covers the problem...

[http://ubuntuforums.org/showthread.php?t=206039](http://ubuntuforums.org/showthread.php?t=206039)

It appears that your home directory has become group writeable, (did you do the restore?...if so, it goofs up the permissions).  

You can fix it with:

```
sudo chown username:username /home/usernmae -R
sudo chmod 740 -R /home/username
```

---

### Post by letmekilluplz on 2009-06-07
```
sean@sean-desktop:~$ sudo chown sean:sean /home/sean -R
chown: cannot access `/home/sean/.gvfs': Permission denied

```

```
sean@sean-desktop:~$ sudo chmod 740 -R /home/sean
chmod: cannot access `/home/sean/.gvfs': Permission denied

```

EDIT - Never mind I just assumed the error messages meant it didn't work but upon logging out then in its working fine.

---

### Post by blueridgedog on 2009-06-07
Excellent.  When you backup to a non Linux file system, then restore, there is no way to preserve file ownership or permission information.  Some programs are sensitive about group writable configuration files and it is generally a good idea to reset your ownship status and basic permission on your files after a restore from such a media.

Good luck!

---

