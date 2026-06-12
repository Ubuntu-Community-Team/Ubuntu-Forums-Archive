---
title: "Any issue with Asus P5V800-MX or VIA P4M800"
date: 2006-06-19
forum: Desktop Environments
---

### Post by ypout on 2006-06-19
Sorry if this is the wrong place for this post.....

I'm looking to buy a new (cheap) PC to run Dapper on, the PC I'm looking at has a Asus P5V800-MX motherboard with the VIA P4M800 and VIA VT8251 chipsets.  I have seen other posts here and on other Linux sites were people have had issues with installing from SATA drives on systems with this motherboard and also other issues with VT8251 chipset.  I have also read that the 2.6.15 kernel has support for the VT8251 chipset. 

I would like to know / confirm:
a) does dapper ship with 2.6.15?
b) does 2.6.15 support the VT8251 chipset?
c) has anyone installed Dapper on a machine with the Asus P5V800-MX motherboard, if so, how did it go?
d) any other advice...

Thanks,

---

### Post by jamuir on 2006-06-20
Despite the inclusion of the 2.6.15 ahci.c patch, the Dapper kernel (2.6.15-23.39) does not allow the vt8251 to read sata drives.  If you have a pata drive, then you shouldn't have any trouble.

I posted some info about Dapper and the vt8251 in another [thread]("http://www.ubuntuforums.org/showthread.php?t=196171")

If you search the forums for "vt8251" you'll find out more.  You can also have a look at the VIA forums.

-James

---

### Post by ypout on 2006-06-20
Thanks James, I read your other thread and searched for VT8251 last night. Having read them I think I might just look for another motherboard / chipset.

I'll have quick look at the via forms too before I make a decission.

Thanks again.

---

### Post by eisblitz on 2006-12-14
According to this post everything works well except the SATA raid 1

[http://ubuntuforums.org/showthread.php?t=218786](http://ubuntuforums.org/showthread.php?t=218786)

I'm about to get this board and a P4 3.0GHz combo and won't need raid and don't have sata anything, so i think i'm good.

---

