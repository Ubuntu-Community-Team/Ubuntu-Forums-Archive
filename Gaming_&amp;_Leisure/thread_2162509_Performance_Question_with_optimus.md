---
title: "Performance Question with optimus"
date: 2013-07-14
forum: Gaming &amp; Leisure
---

### Post by Elvish Legion on 2013-07-14
So I'm stuck on a laptop with an nvidia Optimus card (420m/intel 4000hd I believe). I remember trying bumblebee a while back and it was not good so I went back to linux. However I miss the openness of linux and wanted to come back (Provided I can play the couple of games I enjoy)

My laptop has an i5 with 4 gb of ram and the 420m/optimus set up. The games I play are Civ 4/5 (I can go either way both are great) TF2/other source games and mine craft.

Any one have any experience with a similar setup?

Thanks

---

### Post by oldrocker99 on 2013-07-14
Well, nVidia's 3.19 Linux driver has Optimus support, released in April. This thread:
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

tells how to best install it. 

Before you begin:

sudo apt-get install dkms

This will keep you from having to reinstall the nVidia driver after a kernel upgrade.

Also, make sure you know which display manager (the screen you log in on) you're using. It's **probably**  ldm. If you're using gdm, or kdm, take note when you stop X for installation.

---

