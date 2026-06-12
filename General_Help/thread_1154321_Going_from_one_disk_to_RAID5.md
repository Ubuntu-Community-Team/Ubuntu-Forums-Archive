---
title: "Going from one disk to RAID5"
date: 2009-05-09
forum: General Help
---

### Post by kabo on 2009-05-09
Hi!

Here is my current setup on one disk:
/dev/sda1   500MB ext3 /boot
/dev/sda2   50GB XFS /
/dev/sda3  swap
/dev/sda4  949 GB XFS /home

Motherboard: [Asus P5N73-CM]("http://www.asus.com/Product.aspx?P_ID=ASZsnKcWIDPLZdcm")

I would like to purchase two more disks and run RAID5. Can I install the two disks, enter the bios and select disk mode "RAID5" and things will automagically solve themselves? Or should I use some sort of software raid?
Or do I need to install the disks and reinstall OS and everything?

Thanks for any help on this!

---

### Post by fjgaude on 2009-05-09
Gosh, no, nothing will be automatic... you can't boot from software raid5. The BIOS fakeRAID will not permit you to easily install Ubuntu. Lots of reading required to get to where you wish to go. Starting with:

[http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks](http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks)
[http://www.hscripts.com/tutorials/linux-services/mdadm.html](http://www.hscripts.com/tutorials/linux-services/mdadm.html)
[http://linux-raid.osdl.org/index.php/Main_Page](http://linux-raid.osdl.org/index.php/Main_Page)

Happy study time!

---

### Post by kabo on 2009-05-10
> **fjgaude said:**
> Gosh, no, nothing will be automatic... you can't boot from software raid5. The BIOS fakeRAID will not permit you to easily install Ubuntu. Lots of reading required to get to where you wish to go.


Thanks for pointing me in the right direction.

Would this be a feasible plan?
/dev/sda1 500MB ext3 /boot
/dev/sda2 50GB XFS /
/dev/sda3 swap
/dev/sdb1 extra_disk_1
/dev/sdc1 extra_disk_2
/dev/md0 1898 GB XFS /home   <-- sda4+sdb2+sdc2 RAID5 created with mdadm (949GB each)

I'm on Ubuntu 8.04 BTW, forgot to mention that.

But for this to work I need backup my current things in /home, create the RAID and then copy the stuff back right? I couldn't figure out a way to make mdadm convert my partion into a RAID5 with the other disks.

Is all this correct?
Thanks for your help!

---

### Post by fjgaude on 2009-05-10
I know of no way to convert your present drive into a raid5 array.

Your setup is complex... if you have a drive failure you will have a time getting everything back to normal replacing the failed drive.

If you think about some stratergy to get your important data from the present drive onto DVDs or some other device I'd try doing what you wish... take it slowly, learn as you go.

Consider, raid is not an excuse for not having full backup of all things important. I have three levels, one online, another near-line, and finally, one off-line. I have data I cannot afford to lose. Do you? Notice my signature; I'm a graphic designer with artwork impossible to replace.

Good luck!

---

