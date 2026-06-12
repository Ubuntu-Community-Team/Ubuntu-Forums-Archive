---
title: "Writing to ntfs over network"
date: 2006-08-24
forum: Desktop Environments
---

### Post by andyg001 on 2006-08-24
Hi,

I am new to linux but am loving the challenge.  Currently dual booting XP home and Dapper.  I have set up ntfs 3g to read my windows drive and set up my laptop (running xp home) to view these files across the network with samba - BUT i can't write across the network to my ntfs partitions.

i can write to them in Dapper.  I get a permissions error when trying to write from my laptop - any ideas would be greatly received.

cheers

Andy

---

### Post by der_joachim on 2006-08-24
> **andyg001 said:**
> Hi,

I am new to linux but am loving the challenge.  Currently dual booting XP home and Dapper.  I have set up ntfs 3g to read my windows drive and set up my laptop (running xp home) to view these files across the network with samba - BUT i can't write across the network to my ntfs partitions.

i can write to them in Dapper.  I get a permissions error when trying to write from my laptop - any ideas would be greatly received.


Try [this SAMBA documentation page]("https://help.ubuntu.com/ubuntu/serverguide/C/configuring-samba.html"). 

BTW: ntfs 3g is still pretty unstable. To reduce all risks, you had better mount your NTFS partitions read-only. Use at your own risk.

---

