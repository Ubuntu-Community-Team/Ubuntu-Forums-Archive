---
title: "Boot Up bug"
date: 2006-01-17
forum: General Help
---

### Post by swregulator on 2006-01-17
I have a Dell C600 with ubuntu installed.  About a week ago it started acting strange when booting.  When I turn it on, very often I get a message that the system memory has changed and I'm given the option to continue booting or enter setup.  If I continue booting, it then operates very slowly.  If I shutdown and reboot, or if I boot and then reboot, I will not get this message and it will boot normally.  Then when I turn the machine on the next day, I will get the memory changed message again and may have to reboot one or two additional times to get it to boot normally without the message.  

It's hard to believe this is a hardware problem, given how consistent it is.  Has anyone run into such a problem?

---

### Post by dcstar on 2006-01-17
[QUOTE=swregulator]I have a Dell C600 with ubuntu installed.  About a week ago it started acting strange when booting.  When I turn it on, very often I get a message that the system memory has changed and I'm given the option to continue booting or enter setup.  If I continue booting, it then operates very slowly.  If I shutdown and reboot, or if I boot and then reboot, I will not get this message and it will boot normally.  Then when I turn the machine on the next day, I will get the memory changed message again and may have to reboot one or two additional times to get it to boot normally without the message.  

It's hard to believe this is a hardware problem, given how consistent it is.  Has anyone run into such a problem?[/QUOTE]
That is a Dell BIOS message, it has nothing to do with Ubuntu - you have a hardware problem.

---

### Post by thespazzz on 2006-01-17
Either your BIOS has gone out, Your Motherboard is going out, your Ram is going out, or your CMOS battery may need to be replaced.

You can try opening the case and if you have more than one ram stick remove one of them at a time and see if the issue gets fixed.  If you have only one stick or the system won't boot after checking, Swap out ram.  If that dosen't work then your probobly looking at a Motherboard or BIOS issue.

---

### Post by BigBananaMan on 2008-05-17
You can try running a memtest with a Linux live CD.  You can use your Ubuntu disk for this unless you had the alternate CD, then you could just use Knoppix or some other linux live CD. This will at least tell you if your memory is functioning properly.  CMOS batteries are supposed to last 7 years but can go old faster so you might want to change it anyway.  An update for the BIOS might be in order but I would hold that off for a last resort.

[https://help.ubuntu.com/community/MemoryTest](https://help.ubuntu.com/community/MemoryTest)

---

