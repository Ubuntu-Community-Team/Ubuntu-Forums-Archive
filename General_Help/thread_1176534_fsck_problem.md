---
title: "fsck problem?"
date: 2009-06-02
forum: General Help
---

### Post by evencoil on 2009-06-02
I recently had a crash (caused by overheating I think) which required me to do a hard (power off/power on) reboot.

The reboot stalled at fsck and made a log in /var/log/fsck/checkfs:
```

fsck 1.41.3 (12-Oct-2008)
/dev/sdb6: clean, 157412/59678720 files, 151639670/238689745 blocks
/dev/sdb1 is mounted.  e2fsck: Cannot continue, aborting.

```

It seems as though it wasn't able to mount my secondary hard drive located at /dev/sda (which I just use for backup).

I continued with the boot, things seem to work fine but /dev/sda wasn't automatically mounted as it usually is (I have an entry in /etc/fstab for it). I was able to manually mount it and it seemed fine.

However now whenever I try to reboot I get the same issue. How can I get rid of this?

I tried to manually do a fsck on the drive by unmounting it and then running sudo fsck /dev/sda. I got:
```

fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

which is uninterpretable to me, especially since the filesystem on /dev/sda is in fact ext2. Can anyone explain to me what's going on and how to fix it? Thanks.

---

### Post by mcduck on 2009-06-02
> **evencoil said:**
> I recently had a crash (caused by overheating I think) which required me to do a hard (power off/power on) reboot.

The reboot stalled at fsck and made a log in /var/log/fsck/checkfs:
```

fsck 1.41.3 (12-Oct-2008)
/dev/sdb6: clean, 157412/59678720 files, 151639670/238689745 blocks
/dev/sdb1 is mounted.  e2fsck: Cannot continue, aborting.

```

It seems as though it wasn't able to mount my secondary hard drive located at /dev/sda (which I just use for backup).

I continued with the boot, things seem to work fine but /dev/sda wasn't automatically mounted as it usually is (I have an entry in /etc/fstab for it). I was able to manually mount it and it seemed fine.

However now whenever I try to reboot I get the same issue. How can I get rid of this?

I tried to manually do a fsck on the drive by unmounting it and then running sudo fsck /dev/sda. I got:
```

fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

which is uninterpretable to me, especially since the filesystem on /dev/sda is in fact ext2. Can anyone explain to me what's going on and how to fix it? Thanks.
You can't fsck /dev/sda, that's a disk, not a partition. Try "sudo fsck /dev/sda1" to check first partition on that disk.. ;)

---

### Post by evencoil on 2009-06-02
Got it, thanks!

Could you also explain what the difference is between fsck and e2fsck? The reason I was running fsck on the disk and not the partition is because apparently you need to do that with e2fsck? (And I wasn't sure what I was doing in general :) )

---

### Post by mcduck on 2009-06-02
> **evencoil said:**
> Got it, thanks!

Could you also explain what the difference is between fsck and e2fsck? The reason I was running fsck on the disk and not the partition is because apparently you need to do that with e2fsck? (And I wasn't sure what I was doing in general :) )

fsck is a generic command, it detects what file system a partition has, and then calls the appropriate tool for checking it.

So if you run fsck on Ext2/3/4 partition fsck will use e2fsck to check the partition. If you run fsck on a FAT partiton fsck will use dosfsck to do the check and so on.

And no, e2fsck doesn't run on disks either. Disks don't have any file systems so there would be nothing to check.. :)

---

### Post by evencoil on 2009-06-02
got it, thanks again!

---

### Post by lavinog on 2009-06-02
> **evencoil said:**
> I recently had a crash (caused by overheating I think) which required me to do a hard (power off/power on) reboot.


Is this a laptop?
There is a bug being filed regarding cpus overheating
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/370173](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/370173)

---

