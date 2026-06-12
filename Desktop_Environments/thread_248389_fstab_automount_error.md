---
title: "fstab automount error"
date: 2006-09-01
forum: Desktop Environments
---

### Post by kh4nh on 2006-09-01
I just got 10 extra gig from resizing ntfs partition. I used GParted and created the new partition as ext3. I could mounted manually as

            (mount -t ext3 /dev/hda4 /home)

and used this partition **fine**. When I tried to put it in fstab for auto mount as 

            (/dev/hda4  /home  ext3  defaults  0  2)

I got trouble logging in. This is the error message:

"User's $HOME /dmrc file is being ignored. This prevents the dfault session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by others."


################# original fstab ########################
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222     0       0


############# fstab that gives error ##########################
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda4       /home           ext3    defaults        0  2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222     0       0


I would appreciate and thank for any help. Have a good one guys.

---

### Post by yomimono on 2006-09-01
It looks to me like the drive is getting mounted just fine, but GNOME is not able to log in because of some permission problems on your /home directory.  When you mount the drive manually, you are already logged in using files mounted from your / partition, so you don't see the problem.

If you mount the drive manually, log in, and do:
```

ls -la /home

```
what kind of permissions do you see?

---

### Post by aysiu on 2006-09-01
Boot into recovery mode and do ```
cd /home/kh4nh
chown kh4nh:kh4nh .dmrc
chmod 644 .dmrc
reboot
```

---

### Post by kh4nh on 2006-09-01
kh4nh@ubuntu:~ ls -al /home
drwxr-xr-x  4 root   root   4096 2006-06-09 15:50 .
drwxr-xr-x 23 root   root   4096 2006-08-31 00:47 ..
drwxr-xr-x 47 khnh   khnh   4096 2006-09-01 09:54 khnh
kh4nh@ubuntu:~

kh4nh@xubuntu:~$ ls -l .dmrc
-rw------- 1 khnh khnh 26 2006-05-26 16:42 .dmrc
kh4nh@xubuntu:~$

I still could not log in with auto mount. In recovery mode, I could not find .dmrc files in my home directory or /home.

I guess the reason is because .dmrc is on /dev/hda2 and nothing is on /dev/hda4. How would you suggest to overcome this.

thanks yomimono and aysiu alot for your effort,

later

---

### Post by aysiu on 2006-09-01
.dmrc is a hidden file. If you're using Nautilus or Thunar, press Control-H to see it. If you're using Konqueror, press Alt-V, then H.

---

### Post by kh4nh on 2006-09-01
I know it's a hidden file. When i was in the recovery mode terminal, not only .dmrc file is  not there, but all of my folder and files aren't there either when auto mount. I guess when mounting /home to an empty partition, Gnome complaints about the .dmrc file which is not there. I searched around but have not found any solution yet. Thanks for answering

---

### Post by infoseeker on 2006-09-01
When I mount anything under home I always mount it under /home/<user_name>/ 
example:
```
mkdir ~/hda4

```and mount the partition there. Works for me
Your fstab item would be```
/dev/hda4 /home/<user_name>/hda4 ext3 defaults 0 2
```

---

### Post by kh4nh on 2006-09-01
I tried that too, but no go.

---

