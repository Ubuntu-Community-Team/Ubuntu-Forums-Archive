---
title: "How will Breezy cope with a new motherboard?"
date: 2005-11-02
forum: Desktop Environments
---

### Post by Vulpus on 2005-11-02
i want to replace my current very old Celeron motherboard with an up to date Sempron based one.  However, I want to keep my existing hard drives, CD-ROM etc.  Will this leave Breezy confused and bewildered or will it take it all in its stride?

---

### Post by mxyzptlk on 2005-11-02
i suggest to back up your current configuration of breezzy.

then install the new mother and a freshh breezzy instalation since the resources are not the same.

just keep the other configuration only if you have a special device you dont want to install again.

hope it helps

---

### Post by Vulpus on 2005-11-02
[QUOTE=mxyzptlk]i suggest to back up your current configuration of breezzy.

then install the new mother and a freshh breezzy instalation since the resources are not the same.

just keep the other configuration only if you have a special device you dont want to install again.

hope it helps[/QUOTE]

Trouble is I started off with version 5.04 and then did an upgrade to Breezy.  Over the last few weeks and months I have had to do a lot of tweaking and I would rather not go through al that again.  But if i must...:(

---

### Post by RAOF on 2005-11-02
No, you shouldn't have to.  All the kernel modules for your new stuff are already installed, it should be as simple as just turning it on again.  If you change the video card, you might have to dpkg-reconfigure xserver-xorg, but that's about it, I think.

This is good advice for windows, which doesn't install every driver by default, but linux should handle it fine...

---

### Post by az on 2005-11-02
Just be sure that the ide drives are in the same place and hotplug should take care of the rest.  Of course, if you put some modules in /etc/modules so that they load up "by hand" you should remove them.  

I think X will have to be reconfigured because even if you use the same video card, the pci address will most probably change.

---

### Post by wylfing on 2005-11-02
I agree that as long as your disks are physically mounted in the same order, you should be able to pull this off with a surprising minimum of fuss from Ubuntu.

Short story: I once switched a dual-booting Win2K/Ubuntu box from a non-RAID motherboard to a RAID motherboard, and I thought since I had good backups I'd give it a go and see how things went. I don't know if you've ever admined any Windows boxen, but...well, this just isn't done in Windows-land. Windows had a *fit*. I mean, would not boot, freaking out, "bad hardware" or "you have a virus" messages, junk like that. I spent some good long hours on the recovery console and Googling answers before I managed to get things back in order.

On the other hand, Ubuntu booted up, made some module adjustments, and kept right on ticking. No problem at all, really.

---

### Post by briguy on 2005-11-04
I just changed mine - the dpkg-reconfigure was needed, other than that it ran fine.  I did have weird issue with my USB keyboard in that it would only work in certain ports.

---

### Post by Vulpus on 2005-11-04
Thanks for all the advice.  I feel more inclined to go for the upgrade knowing I will (should) not have to re-install everything.  I have done this before with XP on another PC and the only thing I had to do was revalidate it.  so I would have been a little dissapointed if Ubuntu was less intelligent.  But I will see, i will report back on my experiences once i eventually decide on which mobo to go for.

---

