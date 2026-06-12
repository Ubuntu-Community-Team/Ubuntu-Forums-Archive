---
title: "Ubuntu 9.04 installed on external hard drive, but can't see my primary hard drives"
date: 2009-06-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nara8030 on 2009-06-21
Hi,

I had a problem with my Dell desktop.  It has a Raid 0 configured array of 2 hard drives with Vista installed, and I started getting corrupt sector issues.  Then I started getting BSOD errors and I couldn't enter Windows Vista as a result (not even in Safe mode).  I couldn't even do a recovery without getting a BSOD during the process.

So I installed Ubuntu 9.04 on my external Seagate Free Agent External Hard drive and it boots into Ubuntu.  However, I don't see my RAID 0 setup anywhere and I was hoping to access it through Ubuntu to recover some files (possibly) before I get the hard drives replaced.

Could someone please help me figure out what's wrong?  I can see my cd-rom drives and my external hard drive but that's it.

Also how do I connect to the internet?  I plugged in my ethernet cable in the back of my desktop and I see the auto eth0 trying to work but then it eventually gives up and gives me the network sign with a red X on it.

---

### Post by nara8030 on 2009-06-22
My thought is that I accidentally installed Grub on my primary internal hard drive (the Raid 0 array).  Everytime I try to boot the primary hard drive first I get the Grub Error 21.  I tried to boot from the Windows Vista Install Cd and it doesn't see my primary hard drive at all.  However, under repair my computer options, in command prompt I can access the primary hard drive.  So I think I have a corrupt boot loader or something.  any ideas on how I can fix this?  Please, I need some help.

Thanks.

---

