---
title: "Will RAID give me speed?"
date: 2009-01-21
forum: General Help
---

### Post by mrscruffy on 2009-01-21
Hi there,

I recently built a system from bits lying around at home with the odd extra component from fleaBay. 

I installed Ubuntu onto a 12gb drive - I now refer to this as my Ubuntu drive. 
I then added 2x500gb mirrored RAID1 mounted at home. 

I have since found a spare 80gb drive "hanging around". 

Question: 
If created x number of equal partitions on the 80gb drive and mount as a striped RAID device to replace my Ubuntu drive would I get any increase in speed from the striping RAID? 

Or even a slowdown as the single disk will only ever be able to read from one partition at a time? 

p.s. This is purely an exercise in playing "because I can" - I am fully aware that the A in RAID stands for Array :-)

Many thanks

---

### Post by jerrrys on 2009-01-21
Or even a slowdown as the single disk will only ever be able to read from one partition at a time? 

think you answered your own question....

---

### Post by sedawk on 2009-01-21
This will slow down your system heavily!

Reading any file bigger than 4k will create lots of
slow and unnecessary head movements of the drive to
jump between partitions(=stripes).
The read-ahead cache of the hard disk will be totally useless
and this will decrease performance again.
And your hard disk will be aging faster then normally.

Using Raid-0 (with or without striping) is always a risk because
the failure of only one disk is fatal and the improvement in
performance is too low (if any).

Raid-1 is fine as long as your Raid-Controller doesn't freak out
as soon as one disk is broken (I have lots of bad experiences
with expensive RAID-5 (business SCSI-)systems and broken disks ...)

---

### Post by DeMus on 2009-01-21
> **mrscruffy said:**
> Hi there,

I recently built a system from bits lying around at home with the odd extra component from fleaBay. 

I installed Ubuntu onto a 12gb drive - I now refer to this as my Ubuntu drive. 
I then added 2x500gb mirrored RAID1 mounted at home. 

I have since found a spare 80gb drive "hanging around". 

Question: 
If created x number of equal partitions on the 80gb drive and mount as a striped RAID device to replace my Ubuntu drive would I get any increase in speed from the striping RAID? 

Or even a slowdown as the single disk will only ever be able to read from one partition at a time? 

p.s. This is purely an exercise in playing "because I can" - I am fully aware that the A in RAID stands for Array :-)

Many thanks
Raid on one disk will not work. You need atleast two separate disks for that. RAID: _R_edundant data on an _A_rry of _I_ndependent _D_isks
What you can do, is put the original Ubuntu disk and your 80GB disk in a raid configuration. I know you will throw away 80-12 = 68GB but you have RAID.
Making a mirror RAID, RAID 1, is only for having a constant backup of all your data on the disks. With 12 + 80GB you still only have 12GB of disk.
RAID 0 gives you speed. Ideally 2 times the read and write speed. Problem: if one disks dies, your data is gone. Here you have 12 + 12 (of the 80GB disk) = 24GB.
Disadvantge: you have to re-install Ubuntu using a RAID driver. Here stops my story since I know nothing about a RAID driver for Ubuntu.

Success.

---

### Post by Coreigh on 2009-01-21
Demus, 
  RAID (software RAID) on one disk will *work* provided you have enough equal partitions for the RAID you are attempting. BUT it will be SLOW and it will NOT be fault tolerant. So therefore pointless.

semantic argument, not meaning to start a fight ;-)

---

### Post by DeMus on 2009-01-21
> **Coreigh said:**
> Demus, 
  RAID (software RAID) on one disk will *work* provided you have enough equal partitions for the RAID you are attempting. BUT it will be SLOW and it will NOT be fault tolerant. So therefore pointless.

semantic argument, not meaning to start a fight ;-)

I did not know that. Sorry. I just thought since it will not help you save your data because it is all on 1 disk, and it will not give you any speed improvement since it is all on 1 disk it won't work.
Sorry, I was wrong. My apologies.

---

### Post by Slim Odds on 2009-01-21
RAID with one disk is a non-entity.

RAID, by definition, requires multiple disks.

---

### Post by fjgaude on 2009-01-21
I know many of us have already studied this piece but maybe not:

[http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html)

For important data always backup; no amount of raid guarantees data just availability if drives fail. Backup!

---

### Post by mrscruffy on 2009-01-21
> **fjgaude said:**
> 

For important data always backup; no amount of raid guarantees data just availability if drives fail. Backup!

Many thanks all,
I think that is a conclusive response. IT was always going to be an academic exercise anyway!

---

