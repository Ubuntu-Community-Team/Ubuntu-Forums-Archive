---
title: "Can I have 2 linux distros with vista installed?"
date: 2009-05-18
forum: General Help
---

### Post by Zireth ZH on 2009-05-18
Hey.. i got vista installed dual booting with ubuntu...

i want to install in another partition open suse too.. without deleting either vista or ubuntu.. i like open suse too can i do this?

---

### Post by bumanie on 2009-05-18
If you are using grub as the bootloader, you should be able to boot multiple linux disros. Go [here]("http://users.bigpond.net.au/hermanzone/p15.htm") and find the section with this heading - Operating System Entries for Multiple Booting More Linux Systems

I have an extra ubuntu (for testing) chainloaded with another ubuntu and windows. You will most likely have to set up open suse within a ogical partition, unless it is going on another hard drive.

---

### Post by Zireth ZH on 2009-05-18
> **bumanie said:**
> If you are using grub as the bootloader, you should be able to boot multiple linux disros. Go [here]("http://users.bigpond.net.au/hermanzone/p15.htm") and find the section with this heading - Operating System Entries for Multiple Booting More Linux Systems

I have an extra ubuntu (for testing) chainloaded with another ubuntu and windows. You will most likely have to set up open suse within a ogical partition, unless it is going on another hard drive.

how do i setup open suse in a logical partition?

---

### Post by Legace on 2009-05-18
> **Zireth ZH said:**
> how do i setup open suse in a logical partition?


Type in **sudo gparted** in Terminal.
Then you need  to resize a existing patition, and create a new EXT3 partition in the space  that's freed by resize.

Then you can install SUSE to that partition :)

---

### Post by Zireth ZH on 2009-05-18
i do that where? in opne suse when booted with live cd? 

so this is about creating a new ext3 partition? for example i got a partition with windows, one hard driver entirely for backup, programs and stuff in ntfs format, 1 partition so i can install games in there about 30 gbs size i guess, the other half of it i got ubuntu installed... 

can i like take the partition that has games installed in ntfs format and format it to ext3? do i need to do something else? 

i dun want to screw up my ubuntu ..

---

### Post by Legace on 2009-05-18
> **Zireth ZH said:**
> can i like take the partition that has games installed in ntfs format and format it to ext3? do i need to do something else? 

Yes, you can convert it into EXT3 :)
You can do this either on the SUSE (or Ubuntu) live cd, or on Ubuntu, but you need to unmount the partition you are going to convert if you are going to do it straight from Ubuntu.

---

### Post by rbc on 2009-05-18
What bumanie meant was that you can only have four primary partitions. Windows is probably taking up two, Ubuntu another, so this will be the last primary partition you will be allowed. To save you the hassle of changing things around later, it is best to set up the logical partition now. I forget the maximum number of logical drives allowed. You are going to need to do this running the gparted live cd, or use the Ubuntu live cd. Use Gparted Live, to resize one of the primary partiton. In the free space, create an Extended partition, then within that extended partition, create a logical drive (and designate the filesystem type)

---

### Post by Zireth ZH on 2009-05-18
thanks alot guys i will give it a try

---

