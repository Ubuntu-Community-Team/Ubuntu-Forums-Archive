---
title: "Software Raid Issue"
date: 2010-08-04
forum: Desktop Environments
---

### Post by Psycs00 on 2010-08-04
I've been trying to install Ubuntu 10.04 with the alternate cd. The problem im having during the installation is when im configuring the raid.

Hard Drives

2 x 500GB Sata 
1 x 500 GB IDE 

I start off by creating 3 identical partitions for each drive.

Example;
sda - 400GB partition. Primary, Physical Volume for RAID.
sdb - 400GB partition. Primary, Physical Volume for RAID.
sdc - 400GB partition. Primary, Physical Volume for RAID.

After I finish with that I go to Configure Software Raid
Create MD device and then I select each one of those partitions.
I hit Continue then Finish.

After I hit finish nothing happens. No RAID device is created and this is were i've been stuck at. I tossed this up in vmware on my laptop to make sure I was doing this correctly and it works and I can see that it created the RAID device. Any idea why it's not doing it on my main machine?

---

