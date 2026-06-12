---
title: "NVIDIA/i810 dual monitor problems"
date: 2008-05-01
forum: Desktop Environments
---

### Post by bnetownz on 2008-05-01
Hey,

I have recently installed Ubuntu 8.04 and am having some trouble configuring my dual-monitor setup properly.  Both monitors are Dell 2007wpf, primary is running on a single output (DVI) NVIDIA card, while the secondary monitor is to run on the integrated i810 Intel graphics chip set (VGA).

I have spent a number of hours looking around the web and could not find anything that helped.  If someone could point me in the right direction in setting this up it would be appreciated.  I will not paste the xorg.conf file right now, as all it contains is references for a single monitor setup, which is working correctly.

Thanks.

---

### Post by gnuskool on 2008-05-01
Take a look here 
[http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_900](http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_900)

That site is a thinkpad with linux faq, but the i810 section is a mine of info for setting up your xorg.conf file. As you say info is sparse elsewhere, but this worked for me. You can search the site for other intel card types.

---

