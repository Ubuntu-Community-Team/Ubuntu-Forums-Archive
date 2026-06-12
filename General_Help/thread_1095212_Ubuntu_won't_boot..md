---
title: "Ubuntu won't boot."
date: 2009-03-13
forum: General Help
---

### Post by Trekky0623 on 2009-03-13
I've been using Ubuntu for a while now.  However, just recently I've been getting input/output errors.  These have usually been fixed by just restarting.  However, recently I've been booting up and getting this:

The splash screen comes up, doesn't load, and then shows this:

```
Loading, please wait...
mknod: File exists
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/e4736cd0-2c4d-455f-b2d1-a9d1ab950380) = dev(8,6)
kinit: trying to resume from /dev/disk/by-uuid/e4736cd0-2c4d-455f-b2d1-a9d1ab950380
kinit: No resume image, doing normal boot...
mount: mounting /dev/disk/by-uuid/d498a400-4642-4c5b-9e08-7f01240c7386 on /root failed: Invalid argument
mount: mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: mounting on /sys on /root/sys failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found.  Try passing init= bootarg.

Busybox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```

If I wait a while, this also comes up.

```
Splashy ERROR: Timeout (120 sec) occurred while waiting for a message on the Splashy socket
(!) [ 1595:    0.000] --> Caught signal 11 (at 0x6c707377, invalid address) <--
Splashy caught signal number 6. Exiting...
```

If I type "exit", this comes up:

```
/init: line 231: cannot open /root/dev/console: no such file
[  925.495463] Kernel panic - not syncing:  Attempted to kill init!
```

Now, it used to be that I could avoid this problem by popping out the disk drive while booting.  However, now that doesn't even work.  If someone has some insight into how to boot my computer up, please tell me.

---

### Post by heindsight on 2009-03-13
It sounds to me as if your hard drive is failing.

Perhaps try booting from a live CD and do a filesystem check:
```
sudo e2fsck -f /dev/sdXX
```
Where sdXX should be replaced by the name of your root partition. For example, my root partition is /dev/sda1.

If you don't know what your root partition is, then do:
```
sudo fdisk -l
```
and post the output here and we can try to help you figure out what your root partition is...

---

