---
title: "general Hard drive question"
date: 2009-01-22
forum: General Help
---

### Post by Bigneil on 2009-01-22
My main HDD died. i want to buy a replacement. It was all set up with slave and master HDD's and two dvd drives on the IDE channels.  but i see that a lot of the HDD's on ebay and so on are SATA. i know that my motherboard can support SATA, but what are the pro's and cons ?

are there any particular ups and downs associated with ubuntu.?

---

### Post by TheLions on 2009-01-22
SATA has bigger throughput (it little faster), disks are generally cheaper and it got better connector...

more info here:

[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)

---

### Post by jerome1232 on 2009-01-22
cons: There are no con's to sata vs ide/pata.

:)

---

### Post by Bigneil on 2009-01-22
Thanks guys:D

---

### Post by Bigneil on 2009-02-04
OK, i have bought a drive. i opted for a 300 GB sata drive. a few simple connectors and i have it in the computer. But there is a wee glitch. It isn't being recognised. The Motherboard is a Via kt 600+, Im using Hardy.

i didn't see any setting in BIOS, but to be honest i don't know what i am looking for.

do i need some drivers?

---

### Post by Bigneil on 2009-02-04
Bump

---

### Post by demosthenese on 2009-02-04
Does the new drive appear in gparted? If so it may just need formatting.

---

### Post by Bigneil on 2009-02-04
Thanks for your reply, no gparted does not see the drive.

---

### Post by Gizenshya on 2009-02-04
does the BIOS recognize it?

---

### Post by Bigneil on 2009-02-04
No, i don't think so. what would be a surefire way of checking ?

It wasn't listed  with all the ide drives!

---

### Post by Bigneil on 2009-02-04
I have also tried moving the sata cable from one socket to the other.

---

### Post by Gizenshya on 2009-02-04
hmmm...

can you post a link to your motherboard?

we need to know if the BIOS recognizes it first.  because if it doesn't, it would be a waste of time trying to fiddle with an OS.

what sort of things does your BIOS show? Boot Devices?  Boot Device Prioroty?  Master/Slave (and for what categories/tabs)?

Under what 'category' were the IDE drives listed?  What other same-level categories are there on that page?

it might also help to post your BIOS version and maker.  this might allow us to find screenshots online so we can navigate more efficiently.

---

### Post by Bigneil on 2009-02-04
The BIOS has a good range of options available, boot order, sata/scsi, then 3 slots for any number of different devices etc.

Under 'standard cmos settings'  it is showing me the slave and master drives for the two IDE channels. There is also an option under advanced cmos settings to disable and enable the IDE chanels. there is also a sata option which i have 'enabled'.  

I am Going to go Back in quickly and write down its type and version and hopefullyt find more useful info.

---

### Post by Bigneil on 2009-02-04
[http://www.google.co.uk/search?hl=en&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=Phoenix-award+Bios+cmos+setup+utility+V6.00PG&spell=1](http://www.google.co.uk/search?hl=en&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=Phoenix-award+Bios+cmos+setup+utility+V6.00PG&spell=1)


click on the link and it will take you to a google search, there are two pdf's for my motherboard

---

### Post by Bigneil on 2009-02-05
bump

---

### Post by callan79 on 2009-02-05
> **Bigneil said:**
> click on the link and it will take you to a google search, there are two pdf's for my motherboard


Hi Bigneil,

This may help you:

```
sudo lshw
```

That should list practically ALL the hardware in your entire system. Then you can search though it for "ATA DISK" or perhaps "Serial ATA Disk" (I don't have any SATA drives, so I don't know the exact wording).

If you can see your disk there great.

If not, you need to verify that your BIOS can see it.

But regarding the BIOS, ubuntuforums.org probably isn't the best place for those questions. Perhaps it would be cool if you could visit the support forums of your motherboard manufacturer. Once you are familiar with the BIOS, and you can verify 100% that your BIOS can see the drive, then we can help you with your Ubuntu questions :)

If, on the other hand, lshw DOES see the drive, please post back with the output of:

```
sudo fdisk -l
```

Cheers
Callan

---

### Post by ssam on 2009-02-05
is the drive getting any power? the sata data cable does not carry power.

---

