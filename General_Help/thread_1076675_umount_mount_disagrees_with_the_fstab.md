---
title: "umount: mount disagrees with the fstab"
date: 2009-02-21
forum: General Help
---

### Post by W. Irving on 2009-02-21
> umount: /mnt/snigel/alla mount disagrees with the fstab

This is the message I get when attempting to unmount a CIFS share. Both the Gnome disk mounter applet and mount return this message.

The line from /etc/fstab:
```
//192.168.0.100/alla/ /mnt/snigel/alla cifs dirsync,sync,user,auto,iocharset=utf8,file_mode=0744,dir_mode=0775,rw,uid=alla,gid=alla,noexec,credentials=/home/alla/.sambacredentials 0 0
```

mount returns:
```
//192.168.0.100/alla on /mnt/snigel/alla type cifs (rw,mand,noexec,nosuid,nodev)

```

The line from /etc/mtab:
```
//192.168.0.100/alla /mnt/snigel/alla cifs rw,mand,noexec,nosuid,nodev 0 0

```

ls -lh /mnt/snigel:
```
drwxrwxr-x 20 alla alla 0 2009-01-27 00:11 alla
```

I can unmount as superuser, but that defeats the purpose of the disk mounter applet. It is however possible to mount as alla.
The line in fstab is the same I'm using on another computer (also Hardy) on another network, with exceptions for the the use of UNC paths, the credentials, and the different user/groups defined. It works on that one.

What's wrong?

---

### Post by azzid on 2009-05-03
I have the same error with quite a different mount.

```
mattias@trickle:~$ mount crypt
EncFS Password: 
mattias@trickle:~$ umount crypt
umount: /home/mattias/crypt mount disagrees with the fstab
mattias@trickle:~$ sudo umount crypt
[sudo] password for mattias: 
mattias@trickle:~$ 

```
I can mount as 'mattias' but I can only unmount as root.

The mount I am working with is not a network share as above but a encfs mountpoint.

From my /etc/fstab:
```
encfs#/home/mattias/.crypt/ /home/mattias/crypt fuse rw,user,noauto 0 0
```

I found some old articles about this beeing a bug back in 2007, certaintly the fix must have become standard to mount by now?

The bug can be read about here: [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/99437]("https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/99437"). But I don't really dare to apply a two year old patch to my brand new installation...

Anyone know anything about this issue?

---

### Post by W. Irving on 2009-05-03
I eventually gave up trying to solve this and succumbed to using Gnome for mounting the troubling remote file systems, so I don't know if this has been fixed.

Interestingly, as I mentioned, I'm doing the same thing on the same machine but with on a different LAN. In that instance non-root mounting/unmounting works fine:

/etc/fstab:
```
//engels/trotsky-backup /mnt/engels/trotsky-backup cifs dirsync,sync,user,credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0744,dir_mode=0775,auto,rw,noexec,uid=elias,gid=elias 0 0

```

mount:
```
//engels/trotsky-backup on /mnt/engels/trotsky-backup type cifs (rw,mand,noexec,nosuid,nodev,user=elias)
```

/etc/mtab:
```
//engels/trotsky-backup /mnt/engels/trotsky-backup cifs rw,mand,noexec,nosuid,nodev,user=elias 0 0
```

ls -lh /mnt/engels:
```
drwxrwxr-x 1 elias elias 0 2009-02-09 16:22 trotsky-backup

```


Lets me mount and unmount as a regular user..
```
elias@trotsky:~$ umount /mnt/engels/trotsky-backup/
elias@trotsky:~$ mount /mnt/engels/trotsky-backup/
```

..as well as through using the mount applet.

---

### Post by FlekkeN on 2009-06-29
Maybe this is helpful: [http://www.linuxquestions.org/questions/linux-general-1/fstab-allow-regular-user-to-unmount-a-loopback-file-697942/](http://www.linuxquestions.org/questions/linux-general-1/fstab-allow-regular-user-to-unmount-a-loopback-file-697942/)
I have the same problem and i'm trying to solve it.

---

### Post by WilliamSiddall on 2010-11-30
Long dormant thread, but maybe this will help someone else.

Running 10.10. Ordinary user could mount a cifs drive, but got "mount disagrees with the fstab" when unmounting. sudo umount works fine. My solution was to remove the smbfs package. With the package, problems. Without the package, life is good.

Bill Siddall

---

### Post by ak2766 on 2011-06-19
I know - old thread and all...

But I'm having similar problems on Natty Narwhal (11.04) and suggestions here don't help...

Oh well, time to let a sleeping dog lie...  I'll keep using sudo to unmount as the case maybe...

---

### Post by mp035 on 2011-08-03
I also have the same issue.

I have a noauto samba share in fstab.
When I boot up there is a single icon for my share in the nautilus panel, when I click the icon, a second, but different icon appears for the mount, then I get a message saying "Timeout waiting for mount to appear".

If I click the newly appeared icon, I can use the share, but if I try to unmount I get the "umount: /media/thew mount disagrees with the fstab" message.

Not a major issue, but extremely annoying.

---

### Post by bjpbakker on 2011-08-06
For me this issue was solved by changing fstab to match the exact file system as shown in mount.

//<host>/<dir> /mnt/<dir> in fstab showed in mount as //<host>/<dir>/, which resulted in the inability to umount as user. Changing fstab to //<host>/<dir>/ fixed it.

---

### Post by vanadium on 2011-08-06
You probably will need to set the setuid bit of the mount.cifs and umount.cifs binaries to be able to mount/unmount a cifs mount as a normal user (besides having the "user" or "users" option in your fstab).
```

sudo chmod +s $(which mount.cifs) 
sudo chmod +s $(which umount.cifs) 

```

---

### Post by red321 on 2011-08-15
Adding the trailing / to fstab fixes it for me too, thanks bjpbakker.

---

### Post by rkupv on 2011-08-24
> **bjpbakker said:**
> For me this issue was solved by changing fstab to match the exact file system as shown in mount.

//<host>/<dir> /mnt/<dir> in fstab showed in mount as //<host>/<dir>/, which resulted in the inability to umount as user. Changing fstab to //<host>/<dir>/ fixed it.

Thanks!

---

### Post by stafusa on 2011-09-18
> **bjpbakker said:**
> For me this issue was solved by changing fstab to match the exact file system as shown in mount.

//<host>/<dir> /mnt/<dir> in fstab showed in mount as //<host>/<dir>/, which resulted in the inability to umount as user. Changing fstab to //<host>/<dir>/ fixed it.

Thanks a lot indeed!

Now I just need to find out how to have the permissions preserved when copying...

---

### Post by striscio on 2011-09-19
> **red321 said:**
> Adding the trailing / to fstab fixes it for me too, thanks bjpbakker.

For me too!!!!
Thanks a lot

---

### Post by darkkith on 2011-09-29
> **bjpbakker said:**
> For me this issue was solved by changing fstab to match the exact file system as shown in mount.

//<host>/<dir> /mnt/<dir> in fstab showed in mount as //<host>/<dir>/, which resulted in the inability to umount as user. Changing fstab to //<host>/<dir>/ fixed it.

this worked for me, thanks!

---

### Post by zougoulou59 on 2011-10-23
> **bjpbakker said:**
> For me this issue was solved by changing fstab to match the exact file system as shown in mount.

//<host>/<dir> /mnt/<dir> in fstab showed in mount as //<host>/<dir>/, which resulted in the inability to umount as user. Changing fstab to //<host>/<dir>/ fixed it.

Same Here, Thanks !

---

### Post by sachingnair on 2011-12-22
Uninstall usbmount from Synaptic Manager. That's all

---

### Post by killermist on 2011-12-22
I don't know if this is at all related, but for fuse-based mounts, I think the default unmount method is:
```
fusermount -u /mnt/mount-point
```
I don't know if fuse "borrows" root privileges (after verifying you're the right user to ask for the unmount) do perform the unmount.

---

### Post by bkadoctaj on 2012-02-29
> **killermist said:**
> I don't know if this is at all related, but for fuse-based mounts, I think the default unmount method is:
```
fusermount -u /mnt/mount-point
```I don't know if fuse "borrows" root privileges (after verifying you're the right user to ask for the unmount) do perform the unmount.

Thank you for this helpful hint!  The other solution (adding a / to the mount point) may work for remote filesystems but not for bindfs.

This little gem did the trick.  :D

---

