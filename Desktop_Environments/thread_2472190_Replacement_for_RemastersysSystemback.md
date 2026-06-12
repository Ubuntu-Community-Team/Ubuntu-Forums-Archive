---
title: "Replacement for Remastersys/Systemback"
date: 2022-02-20
forum: Desktop Environments
---

### Post by newholm1 on 2022-02-20
Hi all. How do I create a clone of my operating system that I can transfer to my laptop? I used to use Remastersys until it was discontinued. I then switched to Systemback which did not seem to be able to install to my laptop's SSD. I tried to remake the stick but Systemback won't even do that now for some reason! Is there anything that can do the same job? I have tried a few things (Clonezilla, Penguins-eggs, Timeshift, Mondo Rescue and probably more) but they all either do something slightly different than what I want, or just don't seem to be working. Any recommendations? I really just want something that will create a disk image, go onto a USB stick, and be installed on another system. Such a thing must surely exist!

---

### Post by TheFu on 2022-02-20
The problem is that proprietary drivers would be included. If your source system has nvidia GPU drivers step, then you plug that into a system with Intel iGPU, don't expect it to work.

There is a way to use selective backups to create backups that can be used both to make a fresh install of the OS appear with all your settings, programs, and data. Because the first step is a fresh install of the base OS, we don't have the the same issues with drivers for hardware that isn't there and we can change the underlying storage aspects on the new system.  I've even migrated a 32-bit 16.04 ---> 64-bit 20.04 using the same method. Took about 30 minutes, total.

I get that cloning an install is the Windows way.

Now, if you are going to exactly the same machine and the source storage isn't showing any signs of corruption, then you can use ddrescue to make a clone at the whole-disk device level.  This is effectively what clonezilla does ... or you can use cp.  The trick with cp or ddrescue or clonezilla is to boot from a Try Ubuntu (or any ISO boot Linux), then figure out which device is the source and which is the target.

Say we booted from an Ubuntu Mate 20.04 Live ISO.  When we look at the storage devices using:
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```
Hopefully, we'll see 1 disk with a few partitions, perhaps some logical volumes, heck, even encryption containers. These don't need to be unlocked to clone.  Let's call this disk /dev/sdk and the partitions are /dev/sdk1 sdk2 sdk3 sdk4 sdk5. The "whole drive" is sdk. Partition get a number.

We should see another storage device, probably sdl (el), because that is the next free letter.  The letters for devices do change order from time to time. What controls those name are kernel discovery and how quickly the different buses and hardware controllers respond.  Next boot, those could be opposite, so every new connection or reboot, we have to verify the device names.  sdl doesn't have any partitions. That's fine. We will be cloning everything from sdk, including the partition table and all UUIDs. There is a danger in having storage devices that have identical UUIDs in the same computer. Bad things happen, but you said you want a clone.

Anyway, we have a source - sdk - and a target - sdl.  To copy everything form k ---> l, we can use any command that faithfully copies bits.  cp does that.
```
$ sudo cp /dev/sdk /dev/sdl
```
Easy.

Or use ddrescue which has error recovery and retries ...
```
$ sudo ddrescue /dev/sdk /dev/sdl  /tmp/log
```

Peasy. No fancy gui needed. Just any live-boot Linux environment and a little knowledge.

There are a few caveats.  

All the cloning tools have zero error checking. If you ask them to do something foolish, they will - or they will try.  If you try to clone a 2TB HDD into a 2GB SDcard ... the command will start and errors will start being displayed at 2G, but probably keep going for the remaining 1.999TB. Garbage in = garbage out.

If we get the source and target backwards ... that's a great way to wipe the OS. Congratulations! ;(

The block sizes for the source and target storage need to match.  That is typically 512b for storage 2TB and less, but always 4Kb for larger storage.  Don't cross the streams. Just don't. It will turn out badly.  Some 2TB and less sized storage can use 4Kb sectors, but it isn't common.

The target storage has to be at least the size of the source disk.  Anything smaller has undefined results.

If the target is much larger and the partition table is gpt (GUID PT), then the 2nd copy of the table will be placed badly. You'll want to use gdisk or sgdisk to correct that.  GPT is great for so many things that MBR really should be avoided, always, but sometimes we have old disks. I know I do.

If you want to resize the partitions, use gparted AFTER the cloning is complete, but before you try to boot.  If you modify the UUIDs after the cloning (and you should), then you'll likely need to fix the /etc/fstab and perhaps the /etc/crypttab to use the new UUIDs.  I prefer to use LABELs for mounting storage to avoid the UUID memorization junk. Humans are great at memorizing 20+ character hex numbers, but I can remember root-00 and home-00 and swap-00 easily. Use gparted to create a **unique** label for each partition.

I think those are the most important things. Did I miss anything?

If you need to move to a smaller disk, **fsarchiver** can do that, but it works at the partition level, so you'll need to setup the partitions OUTSIDE the tool first.  The target disk needs to be able to hold the files you are pushing there.

---

### Post by yancek on 2022-02-21
>   then switched to Systemback which did not seem to be able to install to my laptop's SSD.

What does that mean?  What happened when you tried to install from the Systemback iso?

---

