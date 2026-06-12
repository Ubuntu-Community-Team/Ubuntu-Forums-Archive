---
title: "unwanted startup script after partition resizing"
date: 2009-05-19
forum: General Help
---

### Post by qunungnauraq on 2009-05-19
After resizing my ubuntu 8.10 boot partition and swap partition using g-parted, during boot the splash runs for a few seconds and changes to script,starting with "loading files needed to boot".I didnt enable script in my startup manager.
What happened and is there a way to get rid of the script. Everything else seems to run as normal. Boot time is about 45 seconds on a dell dimension 4600 2.8Ghz 1Gb ram.

---

### Post by Soul-Sing on 2009-05-19
install startupmanager, and there a quiet boot option.

---

### Post by qunungnauraq on 2009-05-19
I do have startup manager. "Show text during boot" is not enabled. I don't get text during or before splash, only after it runs a couple seconds it changes to text starting with "loading files needed to boot".

---

### Post by colin.p on 2009-05-20
I am waiting for a solution myself. It's nothing too annoying and everything seems to work fine, just curious why the script started to show after adjusting the partition sizes.
However, there is another thread that the start-up script started to show after an update of the kernel (using 8.10) and even after an update to 9.04 and still no change.
Quite sure we will have an answer soon enough. Sure had me worried the first time I booted up after running gparted.

Colin

---

### Post by djodjoman on 2009-06-21
I am having the same issue here, it is annoying ...
The symptons are the same, I formatted some partitions and change the swap location ...

Another annoying thing i am having is that if use the command s2disk to hibernate, it goes ok, if i use the button hibernate, it won't resume, it will make a normal boot ...

I checked the file /etc/initramfs-tools/conf.d/resume and realize that the uuid didn't exist, and changed do the new SWAP uuid ....even though that didn't worked ...

---

### Post by arvindp3 on 2009-11-09
> **djodjoman said:**
> I am having the same issue here, it is annoying ...
The symptons are the same, I formatted some partitions and change the swap location ...

Another annoying thing i am having is that if use the command s2disk to hibernate, it goes ok, if i use the button hibernate, it won't resume, it will make a normal boot ...

I checked the file /etc/initramfs-tools/conf.d/resume and realize that the uuid didn't exist, and changed do the new SWAP uuid ....even though that didn't worked ...
I too have the same problem.  I tried Startup manager and also checked "Quiet Splash" params in the boot line.  The boot was truly silent/quiet after initial installation of 9.04 but the boot messages started appearing after I made some post-installation resizing of one partition.  I have seen some threads elsewhere linking this problem to partition editing using Gparted, but haven't been able to figure out exactly what needs to happen.

---

### Post by arvindp3 on 2009-11-09
> **arvindp3 said:**
> I too have the same problem.  I tried Startup manager and also checked "Quiet Splash" params in the boot line.  The boot was truly silent/quiet after initial installation of 9.04 but the boot messages started appearing after I made some post-installation resizing of one partition.  I have seen some threads elsewhere linking this problem to partition editing using Gparted, but haven't been able to figure out exactly what needs to happen.
Well, this problem seems resolved for me by following advice seen on this thread:

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/205990](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/205990)

Looks like the UUID of swap area got changed while resizing the partitions and that created some inconsistency.    Hope this helps.

---

