---
title: "ioquake3 video problems on Hardy"
date: 2008-05-13
forum: Gaming &amp; Leisure
---

### Post by joemilx on 2008-05-13
When I start ioquake3 most times, I get a garbled screen in a window with OK sound.  I then have to use ctrl/alt/backspace to log out.  Nothing else works.

Occasionally, I get the proper full screen display and can play the game.  No guarantee that it will work the next time I try it.

My config is:  Asus A8V-VM mobo, 4 x 512MB DDR400, 4 x Seagate 160GB SATA drives (root, home, and swap on SDA, RAID5 array (mdadm) on SDB, SDC, and SDD), USB keyboard, USB mouse, ABIT Airpace PCI-E wireless adapter. I am using Madwifi and Wicd to support the wireless. Monitor is a Samsung 941bw running at 1140x900 @ 60 Hz.  Radeon X800 GT using the restricted driver.

I had to use pci=nomsi in grub to get Hardy to boot up properly.    Otherwise using basic Hardy defaults.

I will appreciate any help to debug and fix this problem.  Thanks.

---

### Post by joemilx on 2008-05-13
Solved.  There was some bad info in the /home/xxx/.q3a/baseq3/q3config.cfg file.  I changed the seta for customwidth to 1440 and the seta for customheight to 900.  All is now well.

---

