---
title: "Unable to fsck ext4"
date: 2011-01-24
forum: Desktop Environments
---

### Post by el_jee on 2011-01-24
[SIZE=1]Seems like I misplaced this topic. Should have been in general help. Sorry! Any moderator feel free to move this topic.[/SIZE]

As I was creating a swap partition, something went wrong and I ended creating a much bigger file which consumed all my empty space.
Ubuntu stopped working and now I can't seem to fsck / mount my disk. Currently I'm on a live cd.

fsck will give:
```
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda2
Filesystem mounted or opened exclusively by another program?
```However, the file system is not mounted.

lsof | grep sda gives me:
```
lsof: WARNING: can't stat() tmpfs file system /cow
      Output information may be incomplete.
jbd2/sda2  462       root  cwd   unknown                                /proc/462/cwd (readlink: Permission denied)
jbd2/sda2  462       root  rtd   unknown                                /proc/462/root (readlink: Permission denied)
jbd2/sda2  462       root  txt   unknown                                /proc/462/exe (readlink: Permission denied)
jbd2/sda2  462       root NOFD                                          /proc/462/fd (opendir: Permission denied)
```I seem not to be able to kill process this process (though I'm not sure if I tried correctly: sudo kill -9 462)

In dmesg I found:
```
[    4.449399] EXT4-fs (sda2): INFO: recovery required on readonly filesystem
[    4.449403] EXT4-fs (sda2): write access will be enabled during recovery
[    4.481617] EXT4-fs warning (device sda2): ext4_clear_journal_err: Filesystem error recorded from previous mount: IO failure
[    4.481622] EXT4-fs warning (device sda2): ext4_clear_journal_err: Marking fs in need of filesystem check.
[    4.481649] last sysfs file: /sys/devices/pci0000:00/0000:00:14.1/host0/target0:0:1/0:0:1:0/block/sda/uevent
```In recovery mode I tried to mount the partition, but that just makes the system hang.

Any thoughts on what else there is to try?

---

### Post by el_jee on 2011-01-24
Problem solved! [http://ubuntuforums.org/showthread.php?t=1601810](http://ubuntuforums.org/showthread.php?t=1601810)

Reference for other ppl who might stumble upon the same problem: [http://ubuntuforums.org/showthread.php?t=1601810](http://ubuntuforums.org/showthread.php?t=1601810)

Apparently the ubuntu live cd tries to mount the partition without success, leaving it neither mounted nor accessible for fsck.

Suggested solution is using Slack, which doesn't mount the filesystems. I managed to do it with some Ubuntu distro I still had on a different disk.

---

### Post by aslam on 2011-02-05
I have similar problem. My ubuntu 10.10 ext4 partition is brocken while updating (kernal update)
I tried Slax but not for me Slax does not support ext4 filesystem

---

### Post by DaveQB on 2011-04-23
I have a system in the same boat running Ubuntu 10.10

But I tried systemrescueCD as it has version 1.41.14 of e2fsprogs as I feared [this bug was causing issue]("https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/711799") while using the Ubuntu 10.10 LiveCD. But same issue....fsck says it is mounted.

What version of Slax did you use??

Thanks

---

### Post by knomegnome on 2013-01-07
resurrecting an old thread... ;)

I have a system that was experiencing a serious problem this way, and which I could not reboot due to production issues.

So, I turned off the scsi device directly, and turned it back on, while the system was running. This cleared the access problem and I was able to e2fsck the partition properly.

You can follow the advice here to do that for yourself:

 [http://gurkulindia.com/main/2011/05/linux-dynamically-addremove-scsi-from-linux/](http://gurkulindia.com/main/2011/05/linux-dynamically-addremove-scsi-from-linux/)

Happy Linux'ing!

---

