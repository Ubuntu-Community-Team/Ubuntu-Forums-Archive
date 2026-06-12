---
title: "Ubuntu - Multiple Drives Question."
date: 2009-05-05
forum: General Help
---

### Post by Roasted on 2009-05-05
I just installed 9.04 on a spare computer. One thing I ran into with much earlier versions of Ubuntu (2006 and earlier) is that when I would install Ubuntu with multiple drives, with the 2nd drive being a backup with no OS, that if that drive was ever taken out of the picture, Grub would error out despite nothing being on that spare drive.

So what I started doing was I would install Ubuntu with only 1 drive attached, and later I would boot up with the drives plugged in and add them to fstab. This worked out great.

Today I just tried installing Ubuntu with a secondary drive attached. As a test, I unplugged the secondary drive and booted up. Halfway through the loading of the splash screen I got a black screen with white text, saying File System Check Failed. A Maintenance shell will now be started. Control D will terminate this shell and resume system boot.

If I Control + D, sure enough it loads just fine. But still I have to question why exactly this happens.

---

### Post by dabl on 2009-05-05
Full disclosure -- I am not an engineer.

As I understand the way Linux works, it reads the firmware (BIOS plus firmware on other chips including GPU) and takes its cues from that information, regarding the hardware on your system, including the initial configuration at the time that you install the OS.  So, if at the time of installation you have two hard drives, they will be listed in BIOS, on the IDE or SATA or both buses (as applicable) and will be enumerated by the installer, for Grub, as hd(0) and hd(1), and for Linux as /dev/sda and /dev/sdb.  The installation routine will configure /boot/grub/menu.lst and /etc/fstab according to the drive that you chose to install Linux on.

When you pull a hard drive, most modern BIOSs will detect it at boot time and the list of drives will be different from that point forward.  Upon reading the new BIOS setup, Grub (which is one "OS" [OK, really just a bootloader]) and Linux (which is another OS) will probably both be more or less confused by the change, depending on the particulars of your original configuration and your new configuration.

That's kind of a generic explanation -- the details are pretty much case specific, like issues between IDE and SATA controllers, whether partitions are marked "bootable", etc.  However, it is easy enough to edit /boot/grub/menu.lst and /etc/fstab to incorporate the new configuration -- there are lots of threads with that information.

---

### Post by Roasted on 2009-05-05
That does make sense... I just wasn't sure how it played out because when I boot up the computer when yanking the drive, it requires me to hit F1 to continue, basically acknowledging that yes, I understand the hardware configuration with the hard drives has changed.

Okay fine. I thought that was all it did though. I didn't realize Linux would give any issues with that. Because I know when I install on a single drive and later add the additional drives to fstab, then yank a drive out, I know then it doesn't give me any errors. So that's why I wasn't sure installing with both drives present was any different than installing with 1 and adding the additional drives later.

---

### Post by dabl on 2009-05-05
> **Roasted said:**
> 

when I install on a single drive and later add the additional drives to fstab, then yank a drive out, I know then it doesn't give me any errors.

Au contraire!  If, during the boot sequence, the system does not see each partition and drive that are listed in /etc/fstab, then you will get an fdisk error.  But, you will be allowed to Ctrl-D past it and continue booting.

With these newer BIOS versions, any addition or deletion of a hard drive (except USB drives) is going to be detected during the boot sequence, and Linux will likely throw an error of one kind or another.

On older PCs with a "dumb" BIOS, where you had to enter the hard drive info manually, Linux is oblivious to any added hard drives, unless you updated /etc/fstab with the additional drive & partition information.

---

### Post by Roasted on 2009-05-05
But I still don't get that.

At home, I installed on a single drive and added the drives later to fstab. If I yank a drive and boot, I get no errors, nothing, period... nadda.

At work, I installed with 2 drives present. If I yank a drive and boot, I get the error I posted above.

So, somehow, things are different. Granted these are different kinds of computers, but it's still Ubuntu 9.04....

---

### Post by dabl on 2009-05-06
> **Roasted said:**
> But I still don't get that.

At home, I installed on a single drive and added the drives later to fstab. If I yank a drive and boot, I get no errors, nothing, period... nadda.

At work, I installed with 2 drives present. If I yank a drive and boot, I get the error I posted above.

So, somehow, things are different. Granted these are different kinds of computers, but it's still Ubuntu 9.04....

It's only speculation -- I can't see your system -- but I'm guessing that on your home system, either there's some defect in the /etc/fstab entry, or in the specified mount point, such that the added hard drive was never really mounted in the first place.  If it was never "in" the system, then there would be no error when it was pulled "out" of the system.

---

### Post by Roasted on 2009-05-06
I don't know what to tell you, to be honest... I'm at work now so I can't show you my fstab but I can certainly assure you that my drives do mount automatically to their specified share.

There's /dev/sdb1, /dev/sdc1, /dec/sdd1.

I got the UUID of each drive and mounted them as:

sdb1 = localbackup
sdc1 = storage
sdd1 = storagebackup

all under the /media directory.

I tested it last night out of curiosity. I disconnected storage and storagebackup and booted up. No error. Nothing. Logged into Ubuntu, saw storage/storagebackup were disconnected yet localbackup was connected.

Powered off, plugged em back in, powered up, logged in - no error, no indication that a drive was added/disconnected/anything, and presto... storage/storagebackup were back.

---

### Post by Grenage on 2009-05-06
In my experience ubuntu loads just fine when a non-critical drive isn't present; the only cases where that didn't happen is when a RAID was configured.

---

### Post by Therion on 2009-05-06
> **Roasted said:**
> ... I disconnected storage and storagebackup and booted up. No error. Nothing. Logged into Ubuntu, saw storage/storagebackup were disconnected yet localbackup was connected.

Powered off, plugged em back in, powered up, logged in - no error, no indication that a drive was added/disconnected/anything, and presto... storage/storagebackup were back.
For all intents and purposes that's been my experience as well, since Gutsy anyway.  I've run dual drives on my system for ages and not since Feisty have I had issues with the the slave-drive not auto-mounting properly or GRUB being fickle about it's presence or non-presence.  Nor have I ever had to manually configure my fstab.

---

### Post by Roasted on 2009-05-07
Just curious... kind of off topic but not really... If I somehow hose grub, like I reinstall Vista and it takes out Grub... but then I need to reinstall Grub to take back operation of booting Ubuntu... what's the best way to go about it?

Should I unplug my backup drives and just install on the main drive? Or does grub somehow install bits and pieces of it on the other drives too?

What's the ideal solution?

---

