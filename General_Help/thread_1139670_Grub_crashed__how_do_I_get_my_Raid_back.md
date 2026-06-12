---
title: "Grub crashed : how do I get my Raid back?"
date: 2009-04-27
forum: General Help
---

### Post by aze555666 on 2009-04-27
HI.

I had a ubuntu installed on a soft Raid0. Once I left my home for 3 days, and when I came back, grub was crashed, unable to run. I used a supergrub disk to reinstall it, but it didn't detect the ubuntu on the raid and made a grub menu for my old ubuntu (on a non-raid disk) and windows xp.

Here is how is my system:
- one HDD with windows xp + ubuntu (intrepid which I upgraded to jaunty. I'm currently using it) + swap + data
- I added 2 SSD, on which installed ubuntu (used alternate CD to make a raid0 : 1st ssd has 1GB boot, 1 GB swap 30 GB ubuntu, 2nd SSD has 2GB data 30GB ubuntu)
- Oddly, the alternate CD seems to have used the old HDD to install grub (I wasn't able to boot the PC after removing the HDD)
- grub config files seem to have disappread from the HDD, supergrub didn't find them and reinstalled grub.

Now I can use the ubuntu that is on the HDD, and upgrade it to jaunty ... but I would like to get my raid0 SSD ubuntu back so that I'll be able to upgrade it and use it (don't realy want to install again, and have a little data saved on ssds). Nor ubuntu, neither gparted neither supergrub can detect the raid0 (gparted -> uknown format, even if I know this raid works with ext3!) ! 

How can I get my raid back in grub?
Thanks.

---

### Post by aze555666 on 2009-05-06
up

---

