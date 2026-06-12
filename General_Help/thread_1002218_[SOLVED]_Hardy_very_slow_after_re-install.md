---
title: "[SOLVED] Hardy very slow after re-install"
date: 2008-12-04
forum: General Help
---

### Post by bmxmann on 2008-12-04
Hello

I was recently very tempted to just reinstall XP, or even Vista, but decided to reinstall Ubuntu because I want to learn more about linux.  About 4 days ago my PC failed to boot, throwing an error of exit status 4, and telling me to run fsck manually.  I tried for about 3 days to repair the file system using fsck, as all I read online said that doing so resolved the issue, but after running it from a Live CD, from a repair promt from a server CD, multiple times, and also trying to resize the partion (one of the fix's_, and it still failing, I decided to stop wasting time with it and to just re-install (wife wasnt to happy not having the main PC).

So, I first booted into XP which I keep around for ripping DVD's, and deleted the Hard drive using the admin tools (I have the XP driver installed to read EXT3 partitions).  I then booted the CD and started the install, just formating the newly created blank space, and leaving the old swap partition alone.  all seemed to go well and I was able to boot into Ubuntu, but I noticed that it seemed to be taking alot longer then it used to, but I figured it might be doing something extra, as it was the first boot and login.

Well, It still takes forever, even opening Firefox seems to be a struggle for this thing.  It used to be pretty fast, and while the Specs on it arnt great, they are not far from being horrible (Pentium D dual core OC'ed to 3.ghz with 2GB of Ram and I have a 2 Gb Swap).  I have fully updated it since reinstalling as well.

I have gone and removed some of the services that are defaulted on that i will never use (such as bluetooth), and anything else I could remember from the previous install.  I even went and disabled any of the pretty visuals, which I had all of them running before without any issues.

I was hoping someone could point me in the right direction, the system will just hang quite often even when opening a smaller programs, even sometimes when I am just using firefox without anything else open.

I have watched the system monitor, and the both CPU cores are usually under 10%, with of course spikes if I launch programs, but i wouldnt say it seems to be stressing the hardware.  also in the system monitor it says that only 234.8 MB of the 2GB of ram are being used, and 0 bytes of the swap.  As for processes, the ones with the Highest memory use are firefox, gnome-panel, and nautilus with 55.1MB, 21.9MB, and 18.6MB in that order.

I just started looking at the logs now, but am not sure which is the best one to look at for something like this, so if anyone could let me know that as well, it would be appreciated.

I would post some of the Logs, but I don't want to put a whole bunch of worthless info, so if anyone wants to see a particular one, let me know and i could put it up.

At least I am back up though.


Thanks!

Nick

(That was alot more then I meant to type, sorry)

---

### Post by utsuprainfra on 2008-12-04
I could check memory with:

free -m

Also I would consider hdparm tuning your drive.  Getting a disc error on install never makes me comfortable, and from experience any time you have to retry an install like 4 times (and you try different media copies and images) you may have physical disc problems.

Other approaches would be to try to remove any unnecessary hardware, who knows if there are IRQ conflicts or whatever.  If you can make her lean and mean with bare bones, readd the components piece by piece until you find the culprit.

Let me know how you get by with that approach.

---

### Post by bmxmann on 2008-12-04
Thanks for the response!

I did a free -m and got this 

              total       used       free     shared    buffers     cached
Mem:          2025        616       1409          0         19        355
-/+ buffers/cache:        241       1784
Swap:         1953          0       1953

(Edit: it pushes all of those together, but it says total 2025 used 628 free 1397 shared 0 buffers 20 cached 356)


Which to me looks good, not using very much.

I looked up hdparm on your recommendation, but it seems like this is just for IDE drives?

[http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html](http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html)

I should have mentioned that I have 2 harddrives, both SATA2.

this is my fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdacadaca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         249     2000061   82  Linux swap / Solaris
/dev/sda2   *        5101       29459   195662399    7  HPFS/NTFS
/dev/sda3             250        5100    38965657+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000921b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       31871   256003776   83  Linux
/dev/sdb2   *       31872       60800   232372192+   7  HPFS/NTFS


I did just notice, that my NTFS partition has the boot * next to it, does that matter?  I have grub set to boot by default to ubuntu.

sda3 is the partiton Ubuntu is installed on, the rest are just for storing stuff.

I am going to force it to run a disk check on the next reboot and see if that finds anything, then I will start pulling stuff out and seeing if any of the hardware has died on me.

Thanks again for your suggestions!

Nick

---

### Post by bmxmann on 2008-12-04
I was able to determine that the problem is with the Hard drive that I was installing on, I continued to get bad blocks and fsck was still continuing to fail, though it would still boot at times.

Most places I found said that just fsck would resolve the issue, but that does not seem to be the case for me.

I installed ubuntu on my other hard drive, and it is now back to its normal speed.  Now I just need to get all my information off that HD, in case it dies.

Thanks

Nick

---

