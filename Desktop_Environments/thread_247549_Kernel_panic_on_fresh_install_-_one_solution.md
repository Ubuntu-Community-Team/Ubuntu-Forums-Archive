---
title: "Kernel panic on fresh install - one solution"
date: 2006-08-30
forum: Desktop Environments
---

### Post by Coopsterman321 on 2006-08-30
Saw several variations of this problem and used information from several others to overcome my issue so I figured I would post my solution in case others want to give it a try.

My problem:
Fresh clean non-windows machine.
Latest Ubuntu 6.06 Desktop CD.
Passed memtest, CD check etc.
I could boot fine from the live CD and run the installation to completion. (I told the installer to reformat my entire hard drive.)

On booting my new installation I got the following message:

RAMDISK: ran out of compressed data
invalid compressed format (err=1)
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

and the system hung.


Here's what I found to be the apparent problem:
The initrd in my installation /boot directory was incomplete. When compared to the one on the live CD it was approximately half the size.

My solution:  replace the installation's initrd with the one from the live CD copy that just booted.

Here's how:
(1) Boot to the live CD (I did it in graphic recovery mode but I don't think it would matter).  Do not run through the installation again.
(2) Open a terminal from the applications menu
(3) Make a dummy directory in /tmp and mount the hard drive's root partition there for 'surgery':
   mkdir /tmp/dumbdir
   sudo chmod 777 /tmp/dumbdir
   sudo mount -t ext3 /dev/hda1 /tmp/dumbdir
   cd /tmp/dumbdir/boot
(4) Rename the bad initrd:
   sudo mv initrd* initrd.old
(5) Copy in the one from the live boot:
   sudo cp /boot/initrd* .
(6) exit from the terminal session and shutdown.  (Remove the CD)
(7) Start and boot up into blissful Ubuntu goodness.  Happy happy joy joy!

Hope this helps!

---

### Post by ChrisC on 2006-09-19
I'm having the same problem with a k7 kernel -- "RAMDISK: ran out of compressed data" et cetera.  And the fact that you found some incomplete file structures rings a bell LOUD for me ...

I rebooted after the update, and the kernel failed per the above.  Then I rebooted using an older kernel (via grub menu), and once it booted up completely there was a popup warning that my /boot partition WAS FULL!  I posted in another forum here about how to cleanly make some space and someone suggested simply removing some of the older kernels via Synaptic.  I did that and now I have a lot more space in /boot (and next time I build a machine I'll give the /boot partition more than 0.1 GB).

But I've still got the problem above (can't boot to newest kernel), probably due to the partition filling up during the install (and I'm disappointed that it didn't warn me about the partition filling up, duh).  So what's the cleanest way to fix it?

I'm thinking using Synaptic to remove the newest kernel, then add it back in again.  Will this work if the original installation was incomplete (due to the partition filling up)?

---

### Post by ChrisC on 2006-09-20
Let me bump this up and restate the question in much shorter form:

Can I use Synaptic to remove the newest kernel (not working, booted on old kernel) if the original installation of it was incomplete (in this case, due to the partition filling up)?

Or will the un-install fail in horrible new ways since it wasn't installed completely in the first place?

---

### Post by ChrisC on 2006-09-21
... waves arms, grabs attention ...

---

### Post by sharm on 2006-09-21
> **ChrisC said:**
> I rebooted after the update, and the kernel failed per the above.  Then I rebooted using an older kernel (via grub menu), and once it booted up completely there was a popup warning that my /boot partition WAS FULL!

Thanks for the tip!  I had this problem this morning and couldn't figure out what was going on (I didn't get any sort of notification that /boot was full).  This is what I did to fix it:

1. Removed old kernels to clear space
2. Went to Synaptic, searched for "2.6.15-27", which was the version that gave me the problems.
3. Selected the four installed packages that showed up, and marked them for re-installation.
4. Applied my changes, rebooted, and all was right with the world.

I didn't want to remove the packages because they seemed to be linked to other packages that I didn't feel comfortable removing (like the "linux-image-686" package, etc).

Hope this helps,
Sandy

---

### Post by ChrisC on 2006-09-25
Re-installation did it!  Thanks!

My graphical mode wouldn't work (got the big blue error screens), despite apparently having the latest packages including linux-restricted-modules.  I suspected that that l-r-m probably got hit by the same full-partition problem, so I did a re-install of that package too and now GUI mode works too.

Thanks sharm!

I sure wish we would get a notification when /boot was filling up during an update session (a security update!).  Bad computer!

---

### Post by Colly on 2006-09-25
I got even less: "Kernel panic! Attempting to terminate init."
Then it all hung. Very consistently on every attempt.
I troubleshot the problem by trying to install Win98 on the same PC (suspecting a wierd hardware problem on this junk PC I'm refurbishing), I got a Windows error message "SU99407" during the setup installation and found a web forum where someone said they had the same message and replaced the mother board. I thought, "Well, I don't have another mobo, but I DO have another CPU".  When I swapped the CPUs everything went just smooth as silk.  Turns out the old CPU had a cooling kit that looked like it had been installed by a drunk auto mechanic.  Oversized screws driven through the CPU board to the heatsink.  It probably shouldn't have been able to boot up at all.

The PC is now busy installing Ubuntu as I type, with no further problems.  I just wish it had been the 300Mhz Celeron that was damaged instead of the 500Mhz PIII (sigh).

So, in my case, the Kernel panic and attempt to abort init were a hardware problem based in the CPU damaged by a clumsy heat sink installation.  On the bright side, the fault is why a friend GAVE me this PC in the first place.

---

