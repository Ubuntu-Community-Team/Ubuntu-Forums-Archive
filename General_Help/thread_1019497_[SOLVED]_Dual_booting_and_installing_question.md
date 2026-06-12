---
title: "[SOLVED] Dual booting and installing question"
date: 2008-12-23
forum: General Help
---

### Post by flatlinecoder on 2008-12-23
I have currently been using Ubuntu 8.10 for about 3 months now I think. I love it, very robust OS and I currently have install a visualization of xp also to run a few programs like Microsoft Visual C++ 2008 Express Edition and photoshop. It all works great, but yesterday I decided to play a few games. I tried using wine and the visualization. Wine worked, but very slow and some graphic glitchs and visualization kept asking for serials and just couldn't get it going.

Currently I have 2 hard drives in my computer, but only using one for ubuntu. The other one is just sitting there with no partitions or nothing on it.

So I was thinking I will install windows xp or maybe even vista on this secound harddrive and then when I want to play games I can boot into that. How would I go about installing and dual booting in this situation? 
I was thinking of just pluging my ubuntu harddrive out and then boot up with windows cd in the drive and install it, but then would this case a problem with GRUB? I really don't know much about this stuff.
Thanks 

Kind Regards
Ciarán

---

### Post by thestig_992 on 2008-12-23
Firstly, I have to warn you NOT TO INSTALL WINDOWS WITH YOUR UBUNTU DRIVE IN. sorry for the caps, but that caused me weeks of issues when my partitions got completely screwed over.

I think that if your BIOS points to your ubuntu drive as the primary drive to boot, then you should be fine, otherwise theres always supergrub disk.

After you get ubuntu booting again, you need to get grub working, which is fairly simple, theres many guides out there that will tell you how to do it.

---

### Post by flatlinecoder on 2008-12-23
> **thestig_992 said:**
> Firstly, I have to warn you NOT TO INSTALL WINDOWS WITH YOUR UBUNTU DRIVE IN. sorry for the caps, but that caused me weeks of issues when my partitions got completely screwed over.

I think that if your BIOS points to your ubuntu drive as the primary drive to boot, then you should be fine, otherwise theres always supergrub disk.

After you get ubuntu booting again, you need to get grub working, which is fairly simple, theres many guides out there that will tell you how to do it.

Thanks for your speedy rely.
Ok so what your saying is that it should be ok to unplug my ubuntu harddrive install windows on the other one. Then plug in both drives and in the bois just choose which drive to be primary drive and it will boot from that one? and am I right in saying GRUB is stored on the HD so that wont coz me any problems when trying to boot into ubuntu?

---

### Post by flatlinecoder on 2008-12-23
Well I just tried that and everything went grand. I didnt brother with any bois settings. I just plug in the harddrive I want to boot from and it works grand. Thanks

---

