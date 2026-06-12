---
title: "DBus error, mount permission"
date: 2009-02-24
forum: General Help
---

### Post by timbalisto on 2009-02-24
I recently had to force a shut down of Windows Vista, but I eventually was able to boot into it to shut down properly. When I boot into Ubuntu, my media partition which is on the same hdd as vista, doesn't auto-mount like normal. I try to mount it but it says, "You are not privileged to mount the volume 'Community Storage'." and after that I get another window that pops up saying, "DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."
Windows Vista is /dev/sda2, Vista's recovery partition is /dev/sda1, and Community Storage is /dev/sda3. Each partition has a warning sign next to them in gparted. I found out that I am able to mount the Vista partition but not Community Storage.
Any help would be appreciated.

---

### Post by geirha on 2009-02-24
The filesystem has probably gotten a dirty flag on it because of the hard shutdown. Try booting Vista and have it run a filesystem check on it. It should mount automatically again after that. 

The reason you get an error when you try to mount it as your user is probably because it has an entry in fstab, and the entry does not include the option to allow regular users to mount it (only root).

---

### Post by timbalisto on 2009-02-24
I did edit fstab to auto mount Community Storage, can changes be made to it to allow non-root to mount it?
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb3
UUID=32cccf65-e896-4e7a-8acc-c46b57b0815d /               ext3    relatime,errors=remount-ro 0       1

# /dev/sda3
UUID=64E5C5544F84B8A7 /media/Community\040Storage ntfs-3g defaults,locale=en_US.UTF-8 0 0

# /dev/sdb5
UUID=244de5fa-d65a-48e6-b367-c41306739ef0 none            swap    sw              0       0
```
and I'll try what you suggested. Thanks.

---

### Post by geirha on 2009-02-24
You currently have the options ```
defaults,locale=en_US.UTF-8
``` You can add either the user or users option to that comma-separated list of options. The difference between the two is explained in mount's man-page:
```

              user   Allow an ordinary user to mount  the  file  system.   The
                     name  of  the mounting user is written to mtab so that he
                     can unmount the file system again.  This  option  implies
                     the  options noexec, nosuid, and nodev (unless overridden
                     by  subsequent   options,   as   in   the   option   line
                     user,exec,dev,suid).

              users  Allow  every  user  to mount and unmount the file system.
                     This option implies the options noexec, nosuid, and nodev
                     (unless  overridden  by  subsequent  options,  as  in the
                     option line users,exec,dev,suid).

```

---

### Post by timbalisto on 2009-02-24
I did a thorough disk check for errors in vista of the media partition, but it couldn't find any problems. I think I'll try adding the 'user' option to fstab, do I add it to the end of the options, or do I put it before or after 'defaults' ? Thanks.

---

### Post by geirha on 2009-02-24
The order of the options does not matter, so you can put it anywhere you like. Once you've saved the new /etc/fstab, run the following in a terminal to test. It should also give a (hopefully) useful error message if it fails. ```
mount -v /media/Community\ Storage
```

---

### Post by timbalisto on 2009-02-24
I saved fstab with the change then tried 
[FONT=monospace]mount -v /media/Community\ Storage

but I got this
[/FONT]```
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://ntfs-3g.org/support.html#unprivileged

```[FONT=monospace]
I'll reboot and try again.
[/FONT]

---

### Post by geirha on 2009-02-24
A reboot won't make a difference. I haven't been fiddling with NTFS for a long while, and apparently things have changed a bit. I don't have enough knowledge about fuse to be able to help you further on that I'm afraid. I think your best bet is to figure out why it doesn't mount automatically at boot instead. What does it say if you try to mount it as root?```
sudo mount -v /media/Community\ Storage
```

---

### Post by timbalisto on 2009-02-24
```
tim@tim-desktop:~$ sudo mount -v /media/Community\ Storage
[sudo] password for tim: 
fuse: failed to access mountpoint /media/Community Storage: No such file or directory

```
That's strange.

---

### Post by geirha on 2009-02-24
Well, just create it and it should get mounted automatically during boot.
```
sudo mkdir /media/Community\ Storage
```

If it gets mounted by gnome-volume-manager, which it does if you double click it in nautilus AND it doesn't have an entry in fstab, then gnome-volume-manager creates the directory first, and then removes it when it gets unmounted. That's probably why it isn't there now.

---

### Post by timbalisto on 2009-02-24
I fixed it! I took its entry out of fstab, rebooted and now it will mount. Now I'll put it back into fstab and see if it will auto mount.
Thanks for all the help.

---

