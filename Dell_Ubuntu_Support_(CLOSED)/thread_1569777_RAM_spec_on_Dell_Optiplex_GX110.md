---
title: "RAM spec on Dell Optiplex GX110"
date: 2010-09-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by colintivy on 2010-09-07
I am trying to install 10.04 on this machine but have been advised that it would be beneficial to increase the 512 Meg RAM to "the maximum". Crucial do not go back that far in their listings, has anyone got the data for the specification of the RAM cards on this machine?? and what would "maximum" mean???

;confused:

---

### Post by mörgæs on 2010-09-07
More memory is always a good idea, but before investing you could also try Lubuntu:

[http://ubuntuforums.org/showpost.php?p=9811956&postcount=4](http://ubuntuforums.org/showpost.php?p=9811956&postcount=4)

It runs well on 512 MB.

---

### Post by cascade9 on 2010-09-07
The specs are here- 

[http://support.dell.com/support/edocs/systems/opgx110/ens/ug/specs.htm](http://support.dell.com/support/edocs/systems/opgx110/ens/ug/specs.htm)

Warning, there are 2 sorts of Optiplex GX110s. One uses socket CPUs, the other uses a CPU slot. It wont make any difference to the memory type though- both use PC100 SDRAM (up to 256MB single stick size) PC133 SDRAM should work as well. 

As for 'the maximum'- Intel limited the i810 chipsets (used in the GX110) to 512MB of RAM. Pity really, but the i810 was always meant to be a 'budget' chipset, the 'perfromance' chipsets for P3 were the 820/820E (super expensive RDRAM or SDRAM, 1GB limit....though I've neer seen a 820 using SDRAM)) or the 840 (RDRAM only, 4GB limit) 

Be thankful you dont have a RDRAM intel chipset...its cheaper to buy a whole new motherboard/CPU/RAM setup than it is to buy RDRAM.....

---

### Post by colintivy on 2010-09-07
Hi cascade9!

Thanks for the post from Oz, been up to Yeppoon via you a year ago.

Link to Spec for the old machine very welcome, I did not know of its existance. Mine is a Low Profile Chassis with all that entails. Surpised that the 512MB is the limit for it, at least it has answered the basic question. The machine has XP on it but the main drive is only 9.52GB which is very limiting. I plan to add a second IDE 160GB drive which will have to be strapped to the original one as there is only one bay for it. Hopefully the power supply at 145W wiil cope.The plan is to keep the XP on its original drive to preserve the association of the OS Serial No with that of the drive to satisfy the lagality to MS and put all the programs and perhaps another OS in dual booting. The associated post above suggests Lubuntu will be OK on 512Mb and I will look into that. 10.04 might be too massive after all, that will have to be the laptop with 8.04 at the moment. This does work with 512MB RAM I am glad to say. Any tips about any of this in your experience?

  :D

---

### Post by mörgæs on 2010-09-07
If possible, best is to mount (with screws, not commands) the hard drives one and one in order to get a better cooling. They are sensitive to heat.

---

### Post by cascade9 on 2010-09-07
Yeppon? LOL, thats somewhere I've never been, and probably never will go to. I really dont like things west of the range, to many rednecks, bevans and associated idiots. What on earth made you leave nice, green wales and go out there to the desolation zone? 

I'd probably flick the 10GB HDD, a 160GB drive would be a lot faster. If you wanted to run both drives, you might remove the floppy drive, depending on if the floppy is 'hidden' (PS/2 style) or exposed. If its exposed, putting a HDD in the floppy drives place would leave a nasty looking hole in the front of the case, unless you can find a 3.5'' panel that actually fits in the dell case. 

Lubuntu should run pretty well on 512MB, or even 256MB. I've got a similar machine that up till recently I was using to play videos, a compaq P3/866, 256MB, 40GB HDD. I used that because smoking next to my 'good'machine seemed a silly idea, but who cares about a compaq I (literally!) picked up on he side of the road? 

BTW, I'm not using lubuntu on that machine. I've tried it, but I dont like LXDE that much. Currently,that machine is running debain Xfce. Xubutnu was awful on that machine, debian Xfce (or ubuntu minimal + Xfce for that matter) runs a lot better.

---

### Post by colintivy on 2010-09-13
Sorry for delay in replying, lots of jobs have intervened (some of SWMBO origin!!). Dell Spec very usefull. I did not expect that to be still available for a 10 year old machine.

Yeppon.. wife's cousin married to GP there. Agree with description as desolate but nice people. We were only passing through on a round-the-world trip, Sydney (friends), Melbourne (another cousin), Hobart (more friends) to name a few!! had a wonderful time but it is now out of our system (& bank balance!!). Green Grass much appreciated now!

Back to matters in hand. My machine is the low profile chassis with the single HD mounted on a bracket and not a tray. It is possible to strap the second HD to the first leaving a decent gap between them as suggested in the post before your last.I can make up flat brackets and holes to match those on the drives. It has been suggested that to avoid upsetting MS by using a drive serial number different from that when XP was first installed it would be beneficial to keep it on the small drive almost on its own and put all the other software on the second HD. In this way we should get the performance boost. I should be able to put enough space in the first partition, say 100GB NTFS, to play with for Winbloat, Swap, Antivirus etc., Then I will put the remainder on to ext3 or 4 for linux, home, swap; also with bags of room to play with that. I am not sure which flavour of Ubuntu right now but I do have CD for 10.04 as well as some earlier ones.

Are there any hidden pitfalls to be avoided in trying to do all this? For instance getting XP to look for everything else on the other drive (presumably D drive)? Similarly will there be any problem in choosing the linux bootloader to run the machine purely as a Linux one?

I am sure that the plot will thicken!

Thanks for help so far.

:D :D

---

