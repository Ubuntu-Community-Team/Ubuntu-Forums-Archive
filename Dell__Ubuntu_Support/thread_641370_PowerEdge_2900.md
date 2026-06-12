---
title: "PowerEdge 2900"
date: 2007-12-15
forum: Dell  Ubuntu Support
---

### Post by s0me1else on 2007-12-15
Hi all,

I got Dell PowerEdge Expandable RAID controller 5i with 5x750GB, but after installation I could not make partition more than 770GB.I know that pe2900 is not supported for debian and ubuntu. Any help would be great.


10x in advance

---

### Post by Francee on 2008-01-23
Hi!

I am looking for a new server, and one of my favourite on my list is the Dell PowerEdge 2900, but i fear little... is it works with ubuntu? 6.06 LTS or 7.10? 

Could you solve your problem, and running a stable server with any kind of ubuntu, debian? or any kind of Linux?

---

### Post by gheeke on 2008-01-24
I've installed two 2900 PowerEdge Servers. One with Ubuntu 7.10 (gutsy) 64-Bit. The other with 7.04 (feisty) 32-Bit. No problems so far.

Maybe the new ubuntu 6.06.2 refresh might also work. I couldn't test it, but the changelog indicates, that they have now included the newer perc raid controllers.

---

### Post by s0me1else on 2008-01-30
Hi guys, 
I installed 7.10 (64 bit), but I did some changes! After I installed the linux erase the old version from parted and I compiled the latest version. 
Then put UUID in the /etc/fstab `cause if you use the normal way /dev/sbd1(for example) from time to time change the mount letters and then ... don't ask what is going to happen.For now all works great.
Now the thing is different. Parted showed me that I've got 2998 GB, but after I mounted  it, it appeared 2.7T. 298GB are gone and where are they? X-Files, the truth is out there, but I am gonna find it :) If someone knows the answer just share it, before I find myself :)

:)

---

