---
title: "RAID 1 Help"
date: 2006-08-13
forum: Desktop Environments
---

### Post by mtdewulf on 2006-08-13
Hi, I have a dedicated file server running dapper and I would like to add two hard drives in a RAID 1 configuration to it.  I will not install the OS on the RAID drive, it will just be used for reliable data storage.  My questions are:

1) Should I do hardware or software RAID given that reliability and ease of use are my biggest concerns?

2) How hard will this be to set up?

3) My motherboard is old and does not support RAID natively, I know I will need a RAID card if I do hardware RAID, will I need one for software RAID as well?

Thanks,
Mike

---

### Post by NetworkGuy on 2006-08-13
Hardware RAID is much faster than software RAID.  But with speed comes a price.  Always use hardware if you can afford it.

It shouldn't be hard but you need to follow the directions to work it.  Since every RAID card is different, it is impossible in this thread to tell you how to configure your card for RAID.

You said you have an older computer.  Make sure the RAID card you get is fully functional with the computer, especially if you decide someday to reload using the mirror set to hold Ubuntu also.

If you use hardware RAID, then there is no reason for software RAID.

Hope this helps.

---

### Post by mtdewulf on 2006-08-13
"You said you have an older computer. Make sure the RAID card you get is fully functional with the computer, especially if you decide someday to reload using the mirror set to hold Ubuntu also."

I was under the impression that I could use most any PCI Hardware RAID card, and that the real compatibility issue would be if Ubuntu supported it?  I.E. that getting RAID to work was more of a matter of OS support.

---

### Post by NetworkGuy on 2006-08-13
Well yes, you should always get hardware that the software will support.  What I was referring to was if you ever plan to rebuild your system and plan on loading your OS on the RAID drives, the BIOS on the card has to work with the BIOS on your MB for the boot process to occur.  

If you plan on just using the RAID set for data only, you shouldn't have to  worry about the BIOS versions.

---

### Post by mtdewulf on 2006-08-13
Thanks.

Last question then: Is there a list of RAID cards known to work with Dapper?  I would like to buy something that other users have had success with.

---

### Post by shahzafar on 2006-08-29
Hi mtdewulf, I am trying to do the exact same thing. I am using an Adaptec 1210SA RAID controller. Were you able to acomplish this? I mean add RAID to an existing server? Can you help me with this?

---

### Post by gerbman on 2006-08-30
You should be able to use 'mdadm' to add software RAID 1 arrays to your system. I use mdadm to administer my RAID 1 system, and have had absolutely no problems with it so far.

---

### Post by cleentrax on 2006-08-30
Software RAID is actually pretty fast for writing, but slower for reading. If you're using ATA drives, make sure they don't share an IDE port, or it will be really slow. mdadm is a good tool.

---

