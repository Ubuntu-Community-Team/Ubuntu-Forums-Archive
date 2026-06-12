---
title: "?script to mount drive in bash"
date: 2009-01-01
forum: General Help
---

### Post by sn0m on 2009-01-01
Hi guys
I'm trying to write a script,that copies some folders in my home directory to a back up drive.
However I'm getting stuck at mounting drive from bash.
This is the script:

#!/bin/bash
#script to back up documents

/bin/mount -t ntfs /dev/sda4 /home/sn0m/disk1

----------------------------------------------------------------------------

cd /home/sn0m

------------------------------------------------------------------------------
#copy experimental folder

/bin/cp -r backup1 /home/sn0m/disk1/backup2

----------------------------------------------------------------------------
#unmount backup drive

/bin/umount disk1

#end


is there a code that mounts drives,I mean a code that makes use of sudo, so the bash script can mount the drive?


Thanks in advance
Sokol

---

### Post by dcstar on 2009-01-01
> **sn0m said:**
> Hi guys
I'm trying to write a script,that copies some folders in my home directory to a back up drive.
However I'm getting stuck at mounting drive from bash.
This is the script:

#!/bin/bash
#script to back up documents

/bin/mount -t ntfs /dev/sda4 /home/sn0m/disk1

----------------------------------------------------------------------------

cd /home/sn0m

------------------------------------------------------------------------------
#copy experimental folder

/bin/cp -r backup1 /home/sn0m/disk1/backup2

----------------------------------------------------------------------------
#unmount backup drive

/bin/umount disk1

#end


is there a code that mounts drives,I mean a code that makes use of sudo, so the bash script can mount the drive?


Thanks in advance
Sokol

Firstly, mount does not need any specification of filesystem type if there already is a fstab entry with all the correct details, and if it is an external drive it should be mounted automagically anyway.

Secondly, if you have problems post the error message so people can try and fix the specific problem.

---

### Post by sn0m on 2009-01-01
Hi David
thanks for your response.
My hard drive has 3 partitions, one ext3 for ubuntu, one back up which is ntfs and another ntfs for winxp. I use the back up partition to copy important files from xp or linux.
All I want to do is copy some important files automatically in my back up drive as I am tired of doing it manually all the time.
When I mount my /dev/sda4 drive, i have to do it using sudo.
So do you know any code line to insert in the bash script like /bin/sudo su  (password) mount etc so the bash can do it automatically...
I hope I am clearer this time.
Regards
Sokol

---

### Post by snova on 2009-01-01
> **sn0m said:**
> So do you know any code line to insert in the bash script like /bin/sudo su  (password) mount etc so the bash can do it automatically...

You could change it to:

```
**sudo** mount -t ntfs /dev/sda4 /home/sn0m/disk1
```

But then you would be prompted for your password when you run it.

---

### Post by fm1234 on 2009-01-01
Don't know about passing a password to sudo (I'm not sure it even makes sense) but have you considered to put the mount in fstab? there you can have several type options to allow no root to mount a device:

> 
              **group**  Allow an ordinary (i.e., non-root) user to mount the file
                     system if one of his groups  matches  the  group  of  the
                     device.  This option implies the options nosuid and nodev
                     (unless overridden  by  subsequent  options,  as  in  the
                     option line group,dev,suid).

              **user**   Allow an ordinary user to mount  the  file  system.   The
                     name  of  the mounting user is written to mtab so that he
                     can unmount the file system again.  This  option  implies
                     the  options noexec, nosuid, and nodev (unless overridden
                     by  subsequent   options,   as   in   the   option   line
                     user,exec,dev,suid).

              **users**  Allow  every  user  to mount and unmount the file system.
                     This option implies the options noexec, nosuid, and nodev
                     (unless  overridden  by  subsequent  options,  as  in the
                     option line users,exec,dev,suid).


Might be worth to look also into autofs.

---

