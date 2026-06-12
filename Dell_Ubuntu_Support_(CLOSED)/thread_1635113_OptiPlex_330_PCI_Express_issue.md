---
title: "OptiPlex 330 PCI Express issue"
date: 2010-12-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Urban Taco on 2010-12-01
Hello. I'm a Linux newbie having some trouble trying to setup a four drive RAID 10 setup. Thanks in advance for any help ... I'm running 10.04.1 Server. 

I have a Dell Optiplex 330 with on board video. I had a Rosewill RC-218 SATA  controller card in the PCI Express slot and the system booted fine. Before I installed the drives I updated the system bios from A00 to A07---the latest available in  Linux---and now the computer won't boot with the SATA card in the PCI  Express slot. 

 I changed the video settings in bios from Auto to OEP when I first  installed the card, under A00. This prevented the computer from thinking  the PCI Express card was a video card. The setting remains the same  now. I've toggled it several times, but still I get a dark screen, the  monitor not recognized. When I pull the PCI Express card everything  works fine, video wise, leading me to believe the system thinks that the PCI Express SATA card is a video card. 
 
 I'm wondering if there's a known fix for this, and if not, can some one point me to directions for downgrading the bios back to A00. I tried the obvious routes to downgrade i.e. followed the upgrade steps and pointed to the old bios files, but the system says, basically, I can't "upgrade" with an older file ... Again, any help is greatly appreciated. 

Thanks.

---

### Post by Urban Taco on 2010-12-02
Anyone know how to rollback Dell BIOS in Ubuntu server? 

Perhaps my title to this post isn't helping ...

---

