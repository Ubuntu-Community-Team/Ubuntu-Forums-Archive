---
title: "&quot;cannot mount volume&quot; hard drive AWOL"
date: 2009-05-05
forum: General Help
---

### Post by alanwalterthomas on 2009-05-05
I (relatively inexperienced) can't mount the hard drive or recover files.

Last night I scp'd ~80GB to my laptop's ~100GB HDD which had just been loaded with 9.04 ext4 to start over from a fresh install with ext4 on my desktop. Meanwhile, the laptop was downloading UNR for a netbook. It had about 10 minutes to go when I wanted to leave it so I downloaded gshutdown at the same time & told it to shutdown after 20 minutes. When I come back in the morning, the computer is off as it should be.

I turn it back on & ubuntu begins to boot (gets past grub) but after a few seconds I get kicked to something like "intrmfs" command line with what look like ext4 or hard disk error messages above it.

Ok, so something's wrong, I boot from the live 9.04 CD & I when I try to mount sda1 (the hard drive) I get:

Cannot mount volume.
Unable to mount the volume.
Details >
mount: worng fs type, bad option, bad superbolck on / dev/sda1, missing codepage or helper program, or other error In some cases useful info is found in syslog - try dmesg | tail or so


So I go to the terminal & type dmesg | tail
I get:
[   97.260050] eth0: no IPv6 routers present
[   108.44661] wlan0: deauthenticated
[  109.473109] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  738.363842] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  788.968720] EXT4-fs: ext4_check_descriptors: Block bitmap for group 640 not in group (block 3158584599)!
[  788.968728] EXT4-fs: group descriptors corrupted!
[  926.350677] EXT4-fs: ext4_check_descriptors: Block bitmap for group 640 not in group (block 3158584599)!
[  926.350685] EXT4-fs: group descriptors corrupted!
[  1814.279532] EXT4-fs: ext4_check_descriptors: Block bitmap for group 640 not in group (block 3158584599)!
[  1814.279532] EXT4-fs: group descriptors corrupted!

Looking in System Log Viewer - syslog had a bunch of stuff written that I could provide if it would help. so in terminal wasn't recognized, whatever it is.

After a little while a little windows appears with the message:
Unable to mount 97.0 GB Media
DBus error org.freedesktop.DBus.Error.NoReply:Message did not receive a reply (timeout by message bus)

Partition Editor in the live CD recognizes /dev/sda as 93.16 GiB with the following partions:
Partition     FS          Size       Used       Unused    Flags
/dev/sda1     ext4        90.30 GiB  82.94 GiB  7.36 GiB  boot
/dev/sda2     extended    2.86 GiB   ---        ---
   /dev/sda5  linux-swap  2.86 GiB   ---        ---

So is it possible to recover the OS &/or all/most of the files on it? The drive doesn't seem to be totally unresponsive.
Could this be ext4 related? It seemed faster when it worked & I thought that although it's not the default fs its inclusion meant it was reliable enough. On the other hand, is it likely that the HDD is failing?

Thanks a lot for any help,

---

### Post by logos34 on 2009-05-05
did you do a filesystem check?

> sudo fsck -fp /dev/sda1

---

### Post by alanwalterthomas on 2009-05-05
Thanks for the reply.
nope, wouldn't know to.
Here's the result:

fsck 1.41.4 (27-Jan-2009)
/dev/sda1: Note: if several inode or block bitmap blocks or part of the inode table require relocation, you may wish to try running e2fsck with the '-b 32768' option first. The problem may lie only with the primary block group descriptors, and the backup block group descriptors may be OK.

/dev/sda1: Block bitmap for group 640 is not in group. (block 3158584599)


/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
           (i.e. without -a or -p options)

That's it.

So I guess I have two options:
sudo e2fsck -b 32768
or
sudo fsck -f /dev/sda1     (just remove the p to run manually?)

What's that next step?

---

### Post by logos34 on 2009-05-05
> **alanwalterthomas said:**
> 
sudo e2fsck -b 32768


run that.  hopefully the superblock are ok.

the -fp on the other were just the options to force check (even if initial report 'clean' and accept all repairs w/o prompts

---

### Post by alanwalterthomas on 2009-05-05
ok, I ran sudo e2fsck -b 32768

All I saw happen on the terminal was it print a usage paragraph & then a set of emergency help options like -p (automatic repair), -n (make no changes to filesystem), -y (assume yes to all questions) etc.

I tried to mount the volume after the command & got the original error.
Anything else I should do?

Thanks,

---

### Post by logos34 on 2009-05-05
no, in qouting you what I meant was run

> sudo e2fsck -b 32768 **/dev/sda1**

thought you'd add that...need to specify the partition.  sorry for not being clearer

---

### Post by alanwalterthomas on 2009-05-05
That worked perfectly. I answered yes to a whole bunch (3 x 722) questions about whether to fix various errors, & at the end, it said the filesystem was modified, & then I could mount the disk.

Many thanks!

now just to check...

what's the best way to test the hard drive to make sure that it's in good shape? It was making a couple clicks it didn't normally make last night, but I figured it was just due to it being used a lot. Also, should I reformat/reinstall with ext3?

Thanks again, that was some very useful & very quick help.

---

### Post by logos34 on 2009-05-06
well, one test would be to mount it or try to boot again...Or run a check with smartctl, in the smartmontools pkg, i.e.:

sudo smartctl -a /dev/sda (prints all smart info on disk)

sudo smartctl -t short /dev/sda (run offline short test)

see 

man smartctl 

for more options

---

### Post by alanwalterthomas on 2009-05-09
Update:
My Laptop is back in good health after following the above instructions, but now the desktop has come down with something at least as bad the day after I installed 9.04 on it, just like before.

On bootup I got the message:

Loading, please wait...
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/fab20358-3085-4932-ac98-e4c778214d75) = dev(8,5)
kinit: trying to resume from /dev/disk/by-uuid/fab203-3085-4932-ac98-e4c778214d75
kinit: No resume image, doing normal boot...
mount: mounting /dev/disk/by-uuid/f086f13d-504d-4f32-b01b-b0de420f232e on /root
failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file
mount: mounting /sys on /root/sys failed: No such file
mount: mounting /proc on /root/proc failed: No such file
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg


Busybox ... initramfs


Not quite the same message, but the same result.
So I go back to my livecd & find I can't mount sda1 (again)
I run (again)
sudo fsck -fp /dev/sda1
sudo e2fsck -by 32768 /dev/sda1
& this time I didn't have to press y 10,000 times.
That fixed my filesystem so I could mount /dev/sda1

I found a post at [https://answers.launchpad.net/ubuntu/+source/grub/+question/63005](https://answers.launchpad.net/ubuntu/+source/grub/+question/63005)
that had some of the same problem. There, I was told to compare the grub menu, fstab, and fdisk -l but what I did was follow instructions at the bottom. (copied below)

Boot from the Live CD.

Run sudo fdisk -l The output will be will be a list of your partitions which you need to identify your root partition (usually this is sda1)

You need to mount that partition to access the files:
sudo mkdir /media/root
sudo mount /dev/sda1 /media/root

Browse to /media/root/boot/grub and look at menu.lst and make sure that references the correct sda# value.
Browse to /media/root/etc/ and look at fstab and see if the values are correct (you can also replace the uuid values with the sda# values in the comments),

If that doesnt work you need to run update-grub from inside your disk so with the drive mounted as above:
sudo chroot /media/root/
sudo update-grub

But I looked at the original & updated grub files & didn't see any difference between them.

Anyway, I restarted & ubuntu came up as it should.

2 similar filesystem-related errors with ext4. Should I open a launchpad account & read up on submitting bugs? I have 9.04 UNR installed on a netbook ssd using ext4 for /boot & JFS for the rest, & it's worked perfectly.

---

