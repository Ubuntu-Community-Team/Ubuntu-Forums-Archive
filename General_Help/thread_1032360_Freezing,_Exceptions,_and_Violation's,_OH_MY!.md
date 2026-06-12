---
title: "Freezing, Exceptions, and Violation's, OH MY!"
date: 2009-01-06
forum: General Help
---

### Post by cdnjay on 2009-01-06
Hello,

I anyone could help me with the following error I would be most appreciative.  It didn't show up on the first boot after install but it did show up on the subsequent boots.  I'm running RAID 1 using two hard drives, one new one old, and a PCI controller card with Ubuntu Server 8.10.

```
[   22.667161] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   22.667233] ata1.00: cmd c8/00:20:8f:ca:d0/00:00:00:00:00/eb tag 0 dma 16384 in
[   22.667235]          res ff/ff:ff:ff:ff:ff/00:00:00:00:00/ff Emask 0x2 (HSM violation)
[   22.667373] ata1.00: status: { Busy }
[   22.667427] ata1.00: error: { ICRC UNC IDNF ABRT }
[   22.667489] ata1: hard resetting link
[   23.010042] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   23.050442] ata1.00: configured for UDMA/100
[   23.050456] ata1: EH complete
```

:confused:

Thanks for any help!

Jason

---

### Post by cdnjay on 2009-01-06
More Details after rebooting again:

```
Jan  6 10:00:13 M155 kernel: [   89.534407] ata3.00: limiting speed to UDMA/66:P
IO4Jan  6 10:00:13 M155 kernel: [   89.534420] ata3.00: exception Emask 0x0 SAct 0x
0 SErr 0x0 action 0x6 frozenJan  6 10:00:13 M155 kernel: [   89.534490] ata3.00: cmd c8/00:a0:17:dd:a1/00:00
:00:00:00/e7 tag 0 dma 81920 inJan  6 10:00:13 M155 kernel: [   89.534492]          res ff/ff:ff:ff:ff:ff/ff:ff
:ff:ff:ff/ff Emask 0x2 (HSM violation)Jan  6 10:00:13 M155 kernel: [   89.534629] ata3.00: status: { Busy }
Jan  6 10:00:13 M155 kernel: [   89.534683] ata3.00: error: { ICRC UNC IDNF ABRT
 }Jan  6 10:00:13 M155 kernel: [   89.534745] ata3: hard resetting link
Jan  6 10:00:13 M155 kernel: [   89.880049] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jan  6 10:00:13 M155 kernel: [   89.941308] ata3.00: configured for UDMA/66
Jan  6 10:00:13 M155 kernel: [   89.941329] ata3: EH complete
```

Jason

---

### Post by bonfire89 on 2009-01-07
I'm getting some similar stuff

ata3.00: status: { busy }


amongst other things.


I know for a fact it is because of one port on my new sata controller.

and I don't think it is defective because I just exchanged the card.

And I have tested with a few drives.... :(

---

### Post by albinootje on 2009-01-07
> **cdnjay said:**
>  I'm running RAID 1 using two hard drives, one new one old, and a PCI controller card with Ubuntu Server 8.10.

I had a bit similar errors with an IDE disk a while ago.

I've just search for "error: { ICRC UNC IDNF ABRT }" in a search-engine, it's surprising how little results there are.

I suggest you ask on the Linux kernel (or IDE) mailinglist, and ask the people there to Cc: you in answers.

Make sure to include enough details about your hardware and kernel,
browse through the archives first to get an idea.
[http://marc.info/?l=linux-kernel](http://marc.info/?l=linux-kernel)
[http://marc.info/?l=linux-ide](http://marc.info/?l=linux-ide)

---

### Post by cdnjay on 2009-01-07
Yesterday I switched out my controller card for a different, slightly better card and I'm no longer having this problem.  What's the model numbers of the cards you're using?

Jason

---

### Post by dye46 on 2011-10-30
I blame the cheapie SABRENT controller I used.  Switched to an SIIG and the errors went away.

--Ken

---

