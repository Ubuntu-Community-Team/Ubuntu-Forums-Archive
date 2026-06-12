---
title: "Software RAID-1"
date: 2010-07-01
forum: Desktop Environments
---

### Post by wanderingarticfox on 2010-07-01
I'm looking for any info/Data on software RAID-1 using the new AMD/ATI 890 chipset MOBO's via Gigabyte.
 I viewed a result via New Egg where A person said that the WD Black 1TB/6.0Gb/s did not link up to a RAID ARRAY but that person did not specify if it was a card;firmware or software.
 Has anyone burned in a 6Gb/s RAID-1 Software Array????????????????
 I want to do this but would like to know if anyone has done this with the WD 1TB Black Edition @ 6Gb/s ????????????????????????????????????:confused:

---

### Post by wanderingarticfox on 2011-02-21
I have spent time researching this since I first posted this topic. I see that the community documentation refers to 9.10 and I am wondering if there have been any advancements since then to the software RAID abilities with Ubuntu. ref. [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID) .
The reason I ask is that I would still like to use this feature but I really need someone with experience and greater working knowledge to let me know if the array will be stable for Update Manager, Kernnel updates, use of Synaptic as well if it will handle Virtual Box and the updates to guest Kernnels. I plan for Host 64-bit Ubuntu, V-Box then guest of 32-bit Ubuntu and or Kubuntu. I realise that my initial post was possibly more of confusing than a real question but I have posted here to leave it out there for others future reference and hope that though long this updated post will get me some responses:). Yhx

---

### Post by wanderingarticfox on 2011-02-22
Well I guess I'm the only one posting here. My research has shown that 'inexpensive' RAID cards are not true RAID Controllers. Because I cannot afford a true RAID controller card it seems that using Ubuntu [Linux] Software RAID is the way to go. I think/hope that it being 'software' it will be more stable and upgrade and update better plus allowing for additions of physical drives down the road. The MOBO 'fakeRAID' is chip-set and BIOS dependant and that is something I think might bite me in the very long term. I think/believe that if the drives are in a software RAID that if I make sure I have a boot sector then I can even move them to another compatible system in the future if need be. However if my thinking is wrong please feel free to let me know. Then again if my thinking is correct please let me know that too.

---

### Post by YesWeCan on 2011-02-22
I use software RAID with 4 WD Caviar Black 1TB disks.

The mobo RAID is principally a means to enable software RAID in Windows. So it adds no value to a linux OS and is best disabled. Ubuntu doesn't officially support it: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Linux RAID is very flexible. It is somewhat explained by the md and mdadm man pages.

---

### Post by deconstrained on 2011-02-22
[quote=wanderingarticfox]I'm looking for any info/Data on software RAID-1 using the new AMD/ATI 890 chipset MOBO's via Gigabyte.
I viewed a result via New Egg where A person said that the WD Black 1TB/6.0Gb/s did not link up to a RAID ARRAY but that person did not specify if it was a card;firmware or software.[/quote]
Software raid is not at all dependent on hardware. You could use the drives in AHCI mode or plain old native SATA/IDE mode, and it wouldn't matter, because all the array interfacing is done by the kernel, hence the name 'software array'.

Also, don't be so hard on your "/" and shift keys. It's nothing but painful for your keyboard and annoying to all of us. And ONE post should suffice. If you have anything to add, edit your original post. It's only understandable for the time difference between your first and second post, because that's over 6 months.

---

### Post by wanderingarticfox on 2011-03-03
Points well noted  and taken, thank you for replies.

---

