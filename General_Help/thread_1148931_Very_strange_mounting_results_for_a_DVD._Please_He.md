---
title: "Very strange mounting results for a DVD. Please Help!"
date: 2009-05-04
forum: General Help
---

### Post by theCSapprentice on 2009-05-04
Okay, here's the story. I come home on summer break and my family gives me this DVD from my grandparents full of family video. But the wrinkle is that it is copy-protected. No big deal I said, confident in my ability to copy the DVD as I have done before with no problems. So I put the disk in the drive and was about ready to play it when I realized that I was missing the CSS removal libraries. Installed them and played the DVD just fine. Then I tried to browse the files on the disk. 

According to the machine there were no files on the disk I had just played. Poking around, I discovered the unhide fstab option and that made the files visible for the root account, but no one else. Thus my delema. I just can't seem to get read access for my normal user account and the mounting results are just plain weird.

Contents of fstab:
```

 # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb3
UUID=b8533580-f9b5-48e6-83c4-5c3df83f34aa /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb2
UUID=4fe8d2dc-30e1-4b53-bb5f-af913f55485f none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 unhide,user,noauto,utf8,exec,umask=000 0       0

#Seperate HOME Partiton/Drive
LABEL=home /home ext3 nodev,nosuid,relatime 0 2

```

Results of mount:
```

/dev/sdb3 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sdc4 on /home type ext3 (rw,nosuid,nodev,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/nathan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nathan)
/dev/scd1 on /media/cdrom0 type udf (ro,nosuid,nodev,unhide,utf8,umask=000,user=nathan)

```

Results of ls -la from /media as root:
```

total 14
drwxr-xr-x  4 root       root       4096 2009-05-04 16:22 .
drwxr-xr-x 20 root       root       4096 2009-02-18 01:12 ..
lrwxrwxrwx  1 root       root          6 2009-01-24 09:15 cdrom -> cdrom0
dr--r--r--  3 4294967295 4294967295   88 2009-03-10 09:52 cdrom0
drwxr-xr-x  2 root       root       4096 2009-01-24 09:15 cdrom1
-rw-r--r--  1 root       root          0 2009-05-04 16:22 .hal-mtab

```

Results of cd to /media/cdrom0 as nathan(my username):
```

bash: cd: cdrom0: Permission denied

```

Results of mount /media/cdrom0 as nathan:
```

mount: block device /dev/scd1 is write-protected, mounting read-only

```

So I have one obvious problem: My user account can't get at the files while root has no problem; and several questions:

     1) Why are the default permissions not 777 as they should be set to with a umask of 000?

     2) When the disk is mounted, what is this unknown user "4294967295" that owns the directory? Shouldn't it be my user, or at least root?

     3) And why can I not enter the directory even though the permissions read 444? At the very least I should be able to traverse into the directory even without +x permissions.


So, that is my problem. Hopefully I can get someone here that knows a thing about finicky file system issues to help me out.

---

### Post by taurus on 2009-05-04
Modify your /etc/fstab and remove the options in red for your CD/DVD drive, /dev/scd1.

```

/dev/scd1       /media/cdrom0   udf,iso9660 **[COLOR="Red"]unhide,[/COLOR]**user,noauto,utf8,exec,**[COLOR="Red"]umask=000[/COLOR]** 0       0

```

Save it and reboot.

---

### Post by Don1500 on 2009-05-04
BUMP for the link. Thanks

---

### Post by theCSapprentice on 2009-05-04
> **taurus said:**
> Modify your /etc/fstab and remove the options in red for your CD/DVD drive, /dev/scd1.

```

/dev/scd1       /media/cdrom0   udf,iso9660 **[COLOR="Red"]unhide,[/COLOR]**user,noauto,utf8,exec,**[COLOR="Red"]umask=000[/COLOR]** 0       0

```

Save it and reboot.

Thanks for the response. I tried what you suggested, which by the way is what my fstab originally looked like, and still no improvement. Root can see everything, the directory is still owned by that unknown user, I still have no permission to descend into the directory from my normal user account. There must be something else going on here.

---

