---
title: "Why can't memorystick mount?"
date: 2006-08-05
forum: Desktop Environments
---

### Post by gilgongo on 2006-08-05
I think (but I'm not sure) that a recent kernel update has made it possible for Kubuntu Dapper to see my USB memorystick reader.

So, I've put the following in /etc/fstab:

/dev/sdb /media/memstick vfat noauto,uid=1000,gid=0,rw,users 0 0

When I stick the stick in, the automount sees it, and I get a "what do you want to do?" dialog. I choose "open in new window."

It then tries to mount it, but brings back:

"mount: wrong fs type, bad option, bad superblock on /dev/sdb, 
missing codepage or other error"

Yet, when I try:

sudo mount -t vfat /dev/sdb1 /media/memstick

it mounts no problem.

Why can't the automount thing (whatever it is) work? There's nothing I can see of any help in /etc/messages:

Aug  5 11:04:40 localhost kernel: [17187361.796000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Aug  5 11:04:40 localhost kernel: [17187361.800000] SCSI device sdb: 31680 512-byte hdwr sectors (16 MB)
Aug  5 11:04:40 localhost kernel: [17187361.804000] sdb: Write Protect is off
Aug  5 11:04:40 localhost kernel: [17187361.816000] SCSI device sdb: 31680 512-byte hdwr sectors (16 MB)
Aug  5 11:04:40 localhost kernel: [17187361.816000] sdb: Write Protect is off
Aug  5 11:04:40 localhost kernel: [17187361.816000]  sdb: sdb1
Aug  5 11:04:40 localhost kernel: [17187361.828000] sd 18:0:0:0: Attached scsi removable disk sdb
Aug  5 11:04:40 localhost kernel: [17187361.828000] sd 18:0:0:0: Attached scsi generic sg1 type 0
Aug  5 11:04:44 localhost kernel: [17187365.680000] VFS: Can't find a valid FAT filesystem on dev sdb.
Aug  5 11:04:44 localhost kernel: [17187365.708000] VFS: Can't find a valid FAT filesystem on dev sdb.

Why can't the kernel find that FAT filesystem, when mount can do so no problem?

I notice also that it seems to be trying to mount /media/sdb, which doesn't exist normally, and isn't the mount point given in fstab. At least, the nautilus URL that is in the location bar of the window is system:/media/sdb.

Hhnnnn! This is so incredibly complicated.

---

### Post by jordilin on 2006-08-05
> 
/dev/sdb /media/memstick vfat noauto,uid=1000,gid=0,rw,users 0 0
I wouldn't put this line in the fstab, as Ubuntu mounts pen drives automatically. Secondly, if the Kernel does not recognize the filesystem type, then I would consider reformatting the pen drive, previous backup of its contents.

---

### Post by mlind on 2006-08-05
Yeah, you don't need a /etc/fstab entry at all, just remove it.
If you for some reason would want one, you should make a custom udev rule for your device.

---

### Post by gilgongo on 2006-08-05
Thanks - I tried removing the fstab entry. Now I get the following from nautilus:

"Cannot mount device: 

mount: can't find /dev/sdb in /etc/fstab or /etc/mtab"

Any ideas what's going on?

---

### Post by mlind on 2006-08-05
> **gilgongo said:**
> Thanks - I tried removing the fstab entry. Now I get the following from nautilus:

"Cannot mount device: 

mount: can't find /dev/sdb in /etc/fstab or /etc/mtab"

Any ideas what's going on?

Are trying to manually mount it? It should *just work* when you plug it in, so don't try to mount it manually.
Just remember to umount it before you remove the device.

---

### Post by tatimmer on 2006-08-30
Did you get your problem solved ?  Does the automount work ?

I have the same problem.  For a month the automount worked fine, but yesterday it stopped.

---

### Post by infoseeker on 2006-08-30
I have 3 USB sticks:

1. Transcend 1Gb (mounts RW, no problems)
2. Canyon 512 Mb (mounts RW, no problems)
3. Twinmos 1Gb (ONLY mounts RO :( )

---

### Post by mlind on 2006-08-30
> **infoseeker said:**
> I have 3 USB sticks:

1. Transcend 1Gb (mounts RW, no problems)
2. Canyon 512 Mb (mounts RW, no problems)
3. Twinmos 1Gb (ONLY mounts RO :( )

What does /var/log/messages or udevmonitor say when you plug in your Twinmos USB stick ?

---

