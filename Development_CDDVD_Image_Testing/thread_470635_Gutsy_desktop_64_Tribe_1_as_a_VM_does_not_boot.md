---
title: "Gutsy desktop 64 Tribe 1 as a VM does not boot"
date: 2007-06-11
forum: Development CD/DVD Image Testing
---

### Post by UBfusion on 2007-06-11
I saw that there were no reports yet for Gutsy-desktop-64 on the ISO testing tracker and so I decided to give it a try as a VM guest under WinXP 64 SP2 and latest VMware (6.00 build 45731)

Unfortunately both Tribe 1 and 20070611 gutsy-desktop-64 did not boot. Immediately after the splash screen and choosing an option to boot, the process hangs with 100% cpu and a blank screen. I even tried the safe graphics install and configuring the Hard Disk as an IDE instead of a SCSI. (Feisty betas seldom had this problem in my setup).

I think it's too early to report this as a bug or in the iso tracker, so please if you use VMware, try replicating this problem and report back.

I'll get the alternate iso and see if I can pinpoint the problem (will also update this post).

UPDATE 1: Selecting "Check the CD for defects" also leads to same results.

UPDATE 2: The alternate iso 64 has the same problem, including  "Check the CD for defects".

Has gutsy a different way of addressing IDE devices (compared to feisty)?

---

### Post by Kelimion on 2007-06-19
Works fine for me.

Host:
- AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ (stepping includes AMD's virtualisation)
- 4x1Gb RAM (dual-channel)
- Feisty
- VMware Workstation 6, build 45731.

Gutsy VM:
- 768 Mb
- 2 Processors assigned
- also enabled Paravirtual Kernel under VM Settings -> Options -> Advanced
- SCSI HDD (0:0) 20Gb
- Gutsy Tribe 1 (updated since)

No problems booting whatsoever.

If the VM image wasn't a bit unwieldy (3.2Gb on disk), I'd upload it for you to have a go at. I attached the .vmx file for this machine, perhaps it can be of some help to you.


I did run into a slightly different problem when installing VMware Tools, though...
-----
The installation of VMware Tools 6.0.0 build-45731 for Linux completed successfully.

**Then on configuring VMware Tools:**

Trying to find a suitable vmmemctl module for your running kernel.

None of the pre-built vmmemctl modules for VMware Tools is suitable for your running kernel. Do you want this program to try to build the vmmemctl module for your system (you need to have a C compiler installed on your system)? 
[yes] 

**After building it:**

cp -f vmhgfs.ko ./../vmhgfs.o
make: Leaving directory `/tmp/vmware-config0/vmhgfs-only'

Message from syslogd@gutsy at Tue Jun 19 19:29:11 2007 ...
gutsy kernel: [  270.244626] ------------[ cut here ]------------
Unable to make a vmhgfs module that can be loaded in the running kernel:

Message from syslogd@gutsy at Tue Jun 19 19:29:11 2007 ...
gutsy kernel: [  270.245293] invalid opcode: 0000 [1] SMP 
insmod: error inserting '/tmp/vmware-config0/vmhgfs.o': -1 File exists
There is probably a slight difference in the kernel configuration between the set of C header files you specified and your running kernel.  You may want to rebuild a kernel based on that directory, or specify another directory.

The filesystem driver (vmhgfs module) is used only for the shared folder feature. The rest of the software provided by VMware Tools is designed to work independently of this feature.
If you wish to have the shared folders feature, you can install the driver by running vmware-config-tools.pl again after making sure that gcc, binutils, make and the kernel sources for your running kernel are installed on your machine. 
These packages are available on your distribution's installation CD.

---

### Post by UBfusion on 2007-06-20
Thanks Kelimion for the update. Later daily builds are booting ok and I was planning to post an update here. Then I discovered that even Tribe 1 works, one just has to wait - the mounted iso is taking a really long time to boot and in the meanwhile the hard disk is inactive (I always monitor my hard disks with [FloatLED]("http://www.stone-oakvalley-studios.com/index_software.htm"), a very nice freeware that I'd like to see implemented in linux). The host appeared inactive for more than 40 seconds and so I was fooled to think it was hanged.

It would be very nice if the live cds provided some kind of human friendly feedback right from the start of the boot process (even some nice jokes would be fine), and not just a flashing underscore on the upper left corner of the screen... At least when booting from a burned live cd, you can always hear it spin and guess it's working, but when booting from iso there are no signs of life - just 100% cpu and no hard disk activity.

---

### Post by Kelimion on 2007-06-20
I suppose that since you're on WXP for Host machine you could use Mark Russinovich's [Process Explorer](http://www.microsoft.com/technet/sysinternals/utilities/ProcessExplorer.mspx), to keep an eye on the VMware process (the virtual machine's to be more precise) during boot.

It'll tell you among other things exactly what files and handles it has open. Not quite as exciting as watching paint dry, but perhaps you'll see a few more signs there that it hasn't hung. :D

If nothing else, the tool does make for a very good replacement for WXP's Task Manager.

That said, I'm glad it's worked out for you after all.

---

### Post by ghost_ryder35 on 2007-07-11
> **Kelimion said:**
> I suppose that since you're on WXP for Host machine you could use Mark Russinovich's [Process Explorer](http://www.microsoft.com/technet/sysinternals/utilities/ProcessExplorer.mspx), to keep an eye on the VMware process (the virtual machine's to be more precise) during boot.

It'll tell you among other things exactly what files and handles it has open. Not quite as exciting as watching paint dry, but perhaps you'll see a few more signs there that it hasn't hung. :D

If nothing else, the tool does make for a very good replacement for WXP's Task Manager.

That said, I'm glad it's worked out for you after all.
+1

---

