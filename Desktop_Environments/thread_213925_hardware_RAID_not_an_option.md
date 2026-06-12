---
title: "hardware RAID not an option?"
date: 2006-07-12
forum: Desktop Environments
---

### Post by hotani on 2006-07-12
I just installed a MB that stated it had onboard PATA RAID which i could not find, and SATA RAID which I found in the BIOS but when I booted up with the Live CD it just showed 2 drives as usual. I had them striped in the BIOS setup.

Is it just another "Windows only" thing? Or is there some magic I'm missing out on here?

---

### Post by RAOF on 2006-07-12
> **hotani said:**
> I just installed a MB that stated it had onboard PATA RAID which i could not find, and SATA RAID which I found in the BIOS but when I booted up with the Live CD it just showed 2 drives as usual. I had them striped in the BIOS setup.

Is it just another "Windows only" thing? Or is there some magic I'm missing out on here?
The onboard RAID controlers of motherboards are generally what is called "fakeraid" - they are essentially just normal hard-drive controllers with fancy (windows) drivers, which also write a small amount of configuration to the start of the drives.  In short, hard drives attached to such a controller appear individually in linux (and windows, but the drivers make it appear that they are a single disc, and do all the striping/mirroring/whatever themselves).

You have two options: if you want to dual-boot with Windows, you'll need to set up mdraid (linux software raid).  Check out the [fakeraid howto](https://wiki.ubuntu.com/FakeRaidHowto).

If you **don't** need to dual-boot windows, you can use a better (if you only want to stripe) solution: LVM.  Use the alternate installer CD, and set up LVM in the partitioning options.  The advantage here is that: 
1) LVM will automatically stripe across different physical devices
2) Most disc activities can be done without reformatting, or even rebooting.  For example, if you later added another harddrive, you could (without rebooting) add it to the VG, and extend your existing partitions into the new free space.  Without rebooting.  And it will now start striping across all 3 drives.  Also, you can (in general) **remove** a disc from a VG, also without rebooting.

---

### Post by hotani on 2006-07-12
thanks! I like the sound of that. So should this be done in addition to the MB RAID or instead of? I'm assuming it is an alternative to it, which would be best for me. I will not be dual booting Windows so LVM would do the trick.

I have 2 PATA drives I want to mirror (RAID-1) and the SATA drives I mentioned above for striping. Eventually I want to get a couple more 250s and do RAID-5, but for now it will be a stripe.

---

### Post by RAOF on 2006-07-12
It's instead of MB RAID, and doesn't require any special hardware.  It doesn't even require the discs to be the same size (or in fact be entire discs, it can do the same thing with partitions).

Be aware that LVM doesn't (currenly) support anything but striping at the moment.  If you want to do anything else, use mdraid.

On the other hand, you can use RAID devices created by mdraid as physical discs in LVM, if you want to have a super-array :).  A mirrored set + 2 SATA drives, then everything striped between those 3 devices.  Crazy, eh? :)

Have a look at the [LVM HOWTO]("http://www.tldp.org/HOWTO/LVM-HOWTO/")

---

