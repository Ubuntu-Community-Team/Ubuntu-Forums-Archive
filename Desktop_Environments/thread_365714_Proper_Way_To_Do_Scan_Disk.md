---
title: "Proper Way To Do Scan Disk"
date: 2007-02-20
forum: Desktop Environments
---

### Post by SuperMike on 2007-02-20
I have Breezy Badger still on two systems. Since Feb 13th, both systems have rebooted once or twice daily almost at the same exact times. I don't know if it's a power glitch or perhaps an unstable kernel after an upgrade of the kernel, but that's the symptom.

Well, on bootup tonight, I see that a /home partition (which was separate than the / partition) failed a disk check but appeared to boot fine with no missing files as far as I can tell. So, here's what I want to know:

1) How can I know where the missing files went if the disk check failed?

2) How can I force my system to do a disk check and repair?

3) Are there more risky versions of disk check and repair? I'd rather do the lighter, less risky one first, and then move up to more intensive ones until the disk repair comes back okay.

---

### Post by dcstar on 2007-02-20
> **SuperMike said:**
> I have Breezy Badger still on two systems. Since Feb 13th, both systems have rebooted once or twice daily almost at the same exact times. I don't know if it's a power glitch or perhaps an unstable kernel after an upgrade of the kernel, but that's the symptom.

Well, on bootup tonight, I see that a /home partition (which was separate than the / partition) failed a disk check but appeared to boot fine with no missing files as far as I can tell. So, here's what I want to know:

1) How can I know where the missing files went if the disk check failed?

2) How can I force my system to do a disk check and repair?

3) Are there more risky versions of disk check and repair? I'd rather do the lighter, less risky one first, and then move up to more intensive ones until the disk repair comes back okay.

Edit /etc/default/rcS (I think, check!) and change:
FSCKFIX=yes

Then fsck will run with the "y" option automatically on bootup and fix any errors it finds.

If you have detected errors then there is very little a user can do, apart from allow fsck to clean them up and mark the filesystem as ok.

---

### Post by branbuntu on 2008-05-29
I modified /etc/default/rcS successfully as root and edited the line:
old:
FSCKFIX=no
new:
FSCKFIX=yes

..performed a restart, however a disk check did not perform during the boot-up sequence.

I did some research and have documented an intensive disk check procedure that worked for me.  I will run it again in two months to see if my bad blocks count change.

```

0. Restart, press ESC at the Grub
1. Select Recovery Mode
2. Type df -h            ; identifies which disk is mounted, ie. /dev/sda6
3. Type umount /dev/sda6 ; unmounts the disk
4. Type fsck -pcfv /dev/sda6 
     ; do disk check, the switches assume you have ext2/ext3 filesystem
     ; -p safe repair, fix automatically 
     ; -c use badblocks to do read-only scan
     ; -f force check 
     ; -v good ol' verbose for control freaks
5. My results:
fsck 1.40.7 (Mar xx 2008) and a list if "exception Emask" entries will appear.
On my system, a received over 1500 of these messages.
In summary there were about 1000 bad blocks.
The entire process ran over 10.5 hours for my 210GB Maxtor disk!
6. Type shutdown now -r   ; reboot

```

In my case, the system booted up successfully and I have not detected any data loss or major improvement.

I ran TruImage 8 from a boot disk, and it still reports that my Linux file system has errors, so I assume this is normal.

I will update this message again soon.

Ubuntu 8.04 Hardy. Really, I'm new to this stuff!

---

### Post by SuperMike on 2008-05-30
> **branbuntu said:**
> Hello

If I do this, does it wipe my drive of bad blocks and data as well, or just mark bad blocks, fix broken chains and other easy stuff, and move on (protecting as much as possible of my data)?

---

### Post by aquavitae on 2008-05-30
fsck checks and fixes the file system, not the physical disk, so it won't look at bad blocks. To do that there is a program called (surprisingly!) badblocks. Look at 'man badblocks' to see how to use it.  IIRC, fsck has an option to run badblocks within it. Maybe also have a look at 'man fsck'.

---

