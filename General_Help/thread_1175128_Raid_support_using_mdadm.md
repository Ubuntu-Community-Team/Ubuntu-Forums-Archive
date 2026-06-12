---
title: "Raid support using mdadm"
date: 2009-05-31
forum: General Help
---

### Post by andyvr4 on 2009-05-31
Hey,

I'm looking at setting up a raid based setup on my pc running ubuntu 9.04.  The motherboard is a asus p4c800-e deluxe with 2 sata ports controlled by the southbridge ich5r chipset set and 2 sata ports controlled by the promise PDC20378 controller.

I'm looking at putting 2 sata drives on the ich5r ports and a 3rd on the promise controller and then using raid 0 across all 3 drives for a small (15gB on each drive) partition to use as a boot drive and then raid 5 on the rest of the drives for storage.

Do you guys forsee any major performance problems from running the 3rd drive on the promise controller since it shares the pci bus.  I'm also a little concerned as to rather ubuntu will right out recognize the 3rd drive connected to the promise controller.  Do you guys forsee anything special that I'll half to do in order to get that drive recognized?

For reference I'm planning on using 3 western digital black edition 640gB drives.

Thanks a lot for the help,
Andy

---

### Post by andyvr4 on 2009-05-31
Probably my biggest question relating to this is rather I'm going to need to do anything special to see the drive that is connected to the promise controller are if ubuntu should automatically see it and I assume show it as /dev/sdc.

I would assume things would show up as listed below.
/dev/sda = sata1 port on ich5r
/dev/sdb = sata2 port on ich5r
/dev/sdc = sata1 port on promise

Thanks

---

### Post by andyvr4 on 2009-06-01
One additional question.  How do you guys think the performance of the raid 5 array will be considering i'm using a p4 3.0 ghz cpu.

---

### Post by Niva on 2009-06-02
Hello Andy,
I too wish I'd hear answers.  The best way to find out is to run the live cd and see if you can see the drives/partitions you might already have set up on those drives.  

I can tell you for a fact that I have a dual boot system (for years now) which has a RAID 1 set on it which Ubuntu refuses to see without recompiling and installing some ridiculous drivers from Asus.  In my case the RAID 1 drive stores only data, I don't use it for booting or anything.

Why windows sees the RAID w/o any extra setup is beyond me, but in this case Windows worked much better.

---

### Post by andyvr4 on 2009-06-05
Thanks for the information.  I'm betting that you're using the onboard raid abilities of the promise controller which I'm not planning on.  I'm figuring on just using the 2 sata ports on the promise controller to allow me to connect in more sata drives and then I'll setup a raid 0 between the 2 drives on the ich5r ports and the 3rd drive that's on the promise sata port using mdadm.

From what I've read a raid setup through mdadm should be just about as quick as the raid setup through the promise controller as both are effectively software raids.

---

### Post by Niva on 2009-06-07
Actually I have 6 sata prots, 4 of which are fed by a Marvell controller and the other 2 are through an AMD chip.  I thought this was hardware raid though clearly I could be very wrong.  Overall I have been disappointed in this aspect of my machine and will definitely look into it in more detail.

I've been completely unable to see the RAID drive in linux.  It's an Asus board and they provide linux drivers which require to be compiled.  Now that I'm thinking about it more it seems you're perhaps correct and this is indeed a software raid.

---

### Post by andyvr4 on 2009-06-08
> **Niva said:**
> I've been completely unable to see the RAID drive in linux.  It's an Asus board and they provide linux drivers which require to be compiled.  Now that I'm thinking about it more it seems you're perhaps correct and this is indeed a software raid.

Have you tried using dmraid?  I know a lot of people have had good luck with it, however I haven't personally played with it at all.

I did get 2 of the 640gb WD cavier black's hooked up to the promise sata ports working in ide mode and they appear to work fine with ubuntu using the sata_promise driver with no additional configuration needed, however I'm quite disappointed in the performance.  I've listed several tests that I've done and the resulting speeds below.  All hard drives used where 3 WD 640gb blacks.

CP = Chipset ports
PROM = Promise ports
All speeds where testing using hdparm -t /dev/sd* or hdparm -t /dev/md*
1xCP = 110 MB/sec
1xPROM = 85 MB/sec
2xCP and 1xPROM in RAID0 = 170 MB/sec
1xCP and 2xPROM in RAID0 = 150 MB/sec
2xCP in RAID0 = 210 MB/sec

---

### Post by Krupski on 2009-06-08
> **andyvr4 said:**
> One additional question.  How do you guys think the performance of the raid 5 array will be considering i'm using a p4 3.0 ghz cpu.

It doesn't matter if you have different disk controllers. To Linux, you will simply have /dev/sda, /dev/sdb, etc....

When you add them to the array, you just specify the drives, the number of drives and the array type you want.

For example, to make a RAID 5 array out of 3 drives, you would do:

mdadm -C /dev/md0 -n3 -l5 /dev/sda1 /dev/sdb1 /dev/sdc1

That line means "create an array called '/dev/md0' with 3 drives and make it RAID level 5 and use sda1, sdb1 and sdc1".

The fact that /dev/sda, /dev/sdb or /dev/sdc may be on different controllers is irrelevant.

Note that when you set this up, you do NOT use any hardware RAID. If your add-on card is a RAID card, turn it off and use it JUST as a disk controller. MDADM will take care of all the RAID functions.

Now, here's a suggestion that may save you lots of grief... get yourself a COMPACT FLASH to IDE adapter card (see this [[COLOR="RoyalBlue"]**LINK**[/COLOR]]("http://www.addonics.com/products/flash_memory_reader/adebidecf.asp")).

Get a 2 or 4 GB compact flash card and install Linux on it. Use your disks strictly for data storage.

This way, your system will always boot and work, regardless of whether a RAID drive has failed.

And, being a small "drive", it's easy to backup the CF card using DD and to re-image it if necessary.

Good luck!

-- Roger

---

### Post by andyvr4 on 2009-06-08
Thanks a lot for the great information Krupski!  I had actually figured a lot of that out the hard-way (experimenting), but it would have definitely saved a lot of time just reading that description.  The reason why I was asking about the different controllers wasn't due to wondering if it would work, but more rather wondering if the promise control was supported by linux has I wasn't with the computer when I first posted this thread and I had never used the promise control for any drives before.

Thanks,
Andy

---

### Post by sloggerkhan on 2009-06-08
I use mdadm RAID and it works great.
The thing you need to figure out is if the SATA ports on the PCI card are picked up as normal SATA ports out of the box or if they need to have additional (proprietary) drivers.

If the SATA ports on the additional card work out of the box, then you should be able to do an mdadm raid set up no problems.

---

### Post by andyvr4 on 2009-06-08
> **sloggerkhan said:**
> I use mdadm RAID and it works great.
The thing you need to figure out is if the SATA ports on the PCI card are picked up as normal PCI ports out of the box or if they need to have additional (proprietary) drivers.

Thanks, it turns out that they do work fine.  For anybody that's searching later on the promise 20378 chipset is supported by the sata_promise driver in the linux kernel assuming that you're running the drives in IDE mode.

---

