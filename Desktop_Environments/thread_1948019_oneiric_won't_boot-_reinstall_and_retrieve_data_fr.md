---
title: "oneiric won't boot- reinstall and retrieve data from Deja Dup?"
date: 2012-03-27
forum: Desktop Environments
---

### Post by CJ_Hudson on 2012-03-27
Hi,
I reluctantly admit I will have to reinstall Ubuntu after it refuses to boot any longer (see my thread started here: [http://ubuntuforums.org/showthread.php?t=1942272](http://ubuntuforums.org/showthread.php?t=1942272) ) however, my question to you is, please, once I have reinstalled Ubuntu how easy is it to restore all my files etc. from my last backup with Deja Dup? (assuming I can remember my password- I never thought I'd actually have to use it, I've been running Ubuntu since 2005 and can't ever remember having to do a fresh install because of a serious system error! :-))

---

### Post by QIII on 2012-03-27
I don't think "Nuke 'em from orbit" is the only choice just yet.

If you can get to the recovery mode right now (I realize you were getting all sorts of frustrating behavior based on your previous thread), choose the option to check the disk.  If you get no satisfaction, get back to the recovery mode and start the boot in verbose mode to see where it hangs.

---

### Post by CJ_Hudson on 2012-03-31
Thanks I'll try that.
EDIT:
I got 2 things:
A bash script window accessed from the boot OS selector screen (I have Ubuntu and XP on 1 HD and W7 on a second HD) but didn't know how to run chkdsk from this; and a pink screen with 'resume', 'fsck', 'remount' and 'root' options, which appeared after the verbose boot (result of "Ubuntu with Linux 3.0.0-16-generic (recovery mode)" option in boot menu. Selecting fsck results in the message:

[    13.981642] Adding 4000180k swap on /dev/sda2.     Priority:-1 extents:1 across:4000180k
fsck from util-linux 2.19.1
/dev/sda5: 380102/4653056 files (1.4% non-contiguous), 3305579/18599238 blocks
[   150.566626] EXT3-fs (sda5): using internaljournal

Finished, please press enter

...then I get to another screen offering the following options (with brief explanation omitted here for time's sake) 'resume', 'clean', 'dpkg', 'grub', 'netroot' or 'root'. Please can anyone tell me what 'clean' does, it says it makes empty space or something like that? Not quite sure what it means.

So I selected dpkg (Repair broken packages) and a lot of things scrolled past then it said it was fixing 'libc6'.
Then I updated the grub bootloader then tried to resume normal boot.

 I also previously booted into XP (on same partition as Ubuntu) and ran chkdsk, which reported errors, and ran chkdsk -r on reboot (which it did) in the hope/expectation it would check the WHOLE disk and not just the Windows XP partition, including the Ubuntu secction of the disk! Whew. Any other suggestions gratefully received.

The only other thing I can think of trying is the boot repair disk again since my problems with Ubuntu started after doing a repair/install of W7 on the second HD, and restoring the boot grub menu in order to access Ubuntu.
Please I would really appreciate any further assistance anyone would like to give. 8)

---

### Post by CJ_Hudson on 2012-04-01
Sorry to muliple post my previous post got kinda messy.

 One thing I forgot to mention is the reason I had problems with W7 was because I installed a new CPU and RAM. And W7 at first wouldn't function with the new RAM, UNTIL I put all three sticks (my mobo only recognises 3 GB RAM) contiguously from slots B2 to A2. (I had previously had them from slots A1 to B1 inclusive since B2 is the 'hottest' spot because of the architecture. But as I said W7 refused to boot with this RAM configuration. But Ubuntu, at this stage, was working fine!)
So it could be an issue with Ubuntu with the new configuration of RAM. Or the new CPU.
Incidentally, when one does a 'repair broken packages' in the rescue menu, I assume the desktop has to be connected via a cable to the interent to download the new packages (since the wireless driver has probably not loaded yet)? =)

---

### Post by CJ_Hudson on 2012-04-03
Bump

---

