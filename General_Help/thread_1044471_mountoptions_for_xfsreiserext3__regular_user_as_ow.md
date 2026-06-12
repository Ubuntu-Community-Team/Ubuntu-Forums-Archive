---
title: "mountoptions for xfs/reiser/ext3 / regular user as owner ?"
date: 2009-01-19
forum: General Help
---

### Post by northern lights on 2009-01-19
Folks, I've read the mount( 8 ) manual thrice and I still can't make sense of this:

I have two data partitions that so far had been formatted as vfat (such that they can be accessed from a Windows OS also). The downside is that FAT32 can only handle up to 4gig per file, which results in DVD .isos piling up in /home. I've decided to alter one of the two partition's filesystems.

Here's the problem:
I've tried both reiserfs and xfs and in either case the same occurs. The partition is mounted but owned by root and I don't have permissions to write on it. For my vfat partition, I use the "uid=" mountoption. It works neither with reiser xfs or ext3. What am I doing wrong?

Here's my *fstab*:```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc           /proc           proc    defaults        0       0
/dev/sda2	/               ext3    noatime,errors=remount-ro 0       1
/dev/sda7	/home           ext3    noatime         0       0
/dev/sda9	/media/music	vfat    user,rw,noatime,uid=1000,auto	0       0
[COLOR="Red"]/dev/sda10	/media/storage  reiserfs  user,rw,noatime,auto	0       0[/COLOR]
/dev/sda3      none            swap    sw              0       0
/dev/scd1      /media/dvd-rom  udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0      /media/toaster  udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by Yashiro on 2009-01-19
> I have two data partitions that so far had been formatted as vfat (***such that they can be accessed from a Windows OS also***). The downside is that FAT32 can only handle up to 4gig per file, which results in DVD .isos piling up in /home. I've decided to alter one of the two partition's filesystems.Just use NTFS.

---

### Post by northern lights on 2009-01-19
> **Yashiro said:**
> Just use NTFS.
Windows access is my least worry, just the reason behind having used vfat. As you can see, there's still a vfat partition left, so should I ever have to move data between Linux and Windows, I could.
As for ntfs, I'm trying to avoid the possibility of not being able to mount due to an unclean logfile...

But thank you for your fruitful suggestion.

Plus, the trifling question remains why any fs mounted with *user,rw* should be owned by root and not writeable by a regular user.

---

### Post by adamlau on 2009-01-19
```
chown -R your.login.name /media/storage
```

before:

```
chmod 700  /media/storage
```

---

### Post by northern lights on 2009-01-19
> **adamlau said:**
> ```
chown -R your.login.name /media/storage
```

before:

```
chmod 700  /media/storage
```
Didn't figure chmodding would do the trick. But hey, it did!

Hope it'll prevail past the next reboot.

Still, though solved, I'm wondering why user and rw mountoptions wouldn't suffice.

---

### Post by sisco311 on 2009-01-19
the fat file system doesn't support file permissions.
ntfs supports file permissions, but is not 100% *compatible* with the *linux type* permissions.
[http://pagesperso-orange.fr/b.andre/permissions.html]("http://pagesperso-orange.fr/b.andre/permissions.html")

on this file systems "fake" permissions are set at mount time with the umask,uid,gid... mount options.


on ext3/xfs you can set the permissions of every single file individually with the chmod and chown commands, after the partition is mounted:
[uwiki]FilePermissions[/uwiki]

---

### Post by Yashiro on 2009-01-19
Just out of curiosity did you try not mounting it from your fstab and doing it manually post-boot?

---

### Post by northern lights on 2009-01-19
> **Yashiro said:**
> Just out of curiosity did you try not mounting it from your fstab and doing it manually post-boot?
Manual mounting had always worked.
Just as soon as I added the *auto* mountoption, it got mounted with root as its owner, which, given that *user* and *rw* were used still doesn't make sense to me and/or shouldn't happen in my opinion. *user* apparently just allows a user to mount, but doesn't force automounting to be done as user.

As an aside: Without *auto*, which is included in *defaults* also, even with an *fstab* entry it would have to be mounted manually. Just not with all parameters, but *mount -a* would suffice.

---

