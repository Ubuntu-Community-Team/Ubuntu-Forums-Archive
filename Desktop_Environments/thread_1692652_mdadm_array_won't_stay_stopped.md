---
title: "mdadm array won't stay stopped"
date: 2011-02-21
forum: Desktop Environments
---

### Post by jharris1993 on 2011-02-21
System:
AMD Athlon 64 X2 running Ubuntu 10.04 (x64 and x32)
4 gigs of memory installed.
40 gigs of root disk space with the entire filesystem on the one drive.
I used mdadm to create a RAID-5 array out of four 1T drives.

Setup:
Assume array is assembled and running like a top.
Also assume I want to test something with the array to investigate something weird that just might be my motherboard.

Issue:
Note:  This has happened to me on several systems, using different motherboards, processors and chipsets.  It is irrelevant if the system is running the 64 bit version or the 32 bit version.

Scenario:  I want to stop the array, totally trash it and then rebuild from scratch.
Methodology:  (All done from a root terminal window)
1.  cat /proc/mdstat  (verify that the array is assembled and running)
2.  mdadm --stop /dev/md0  (md0 is the only array on my system)
3.  cat /proc/mdstat  (verify that the array is well and truly stopped.

Next:  Trash MBR and partition table on all drives in array
dd if=/dev/zero of=/dev/sdb bs=512 count=1 
(I hit the device, not the partition, as I want to blow away the partition table)
Using the up-arrow key, I repeat this for ../sdc ../sdd and ../sde

Sometime around the ../sdd or .../sde stage, the array suddenly restarts.
cat /proc/mdstat shows the array running and resyncing.
---------------------------------
I "stop" the RAID array again as I did before, using mdstat to verify that it is well and truly stopped.
I then use System Monitor - as root - to find the mdadm process that is running, and I kill it.

Now, I have a stopped array *AND* I've killed off the process that runs it.  This thing should be SO DEAD that even a homicide detective couldn't get it started again.

Again, I try to zero out the MBR and the first 50 or so megs of each drive, to make the array "disappear"

Issue:
1.  Once I begin writing to the drives, using any method, the array restarts.
2.  I set it so that the array cannot start, (I've pulled three of the four drives, and renamed mdadm.conf, prior to a reboot.) - and then. . .
3.  If I run gparted from within a root terminal (instead of using the icon to launch it), I always get errors saying that it "can't stat /dev/md0"

Questions:
1.  Is there a way to stop an array so that it *stays stopped* until I manually re-start it?
2.  Is there a way to totally kill off (temporarily) the entire array subsystem?  Silver bullet?  Stake through the heart?
3  Having created an array and done some tests, is there a way to absolutely destroy the array
Viz.:  So that mdadm won't complain that these drives look like they're part of any array, and the md device is gone - as if there was never an array there before.

I don't know if these are bugs, or just stupid noob questions.

Any help would be appreciated.

Jim

---

### Post by deconstrained on 2011-02-21
Someone else was having similar problems with mdadm, and [I explained what may be the most likely cause](http://ubuntuforums.org/showthread.php?t=1691907).

Long story short, in Ubuntu mdadm runs as a service by default, and you need to stop/kill it and disassemble/stop the arrays that it haphazardly auto-assembles.

---

