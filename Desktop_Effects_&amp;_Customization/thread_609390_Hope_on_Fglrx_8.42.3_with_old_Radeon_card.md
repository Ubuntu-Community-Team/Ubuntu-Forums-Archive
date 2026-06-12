---
title: "Hope on Fglrx 8.42.3 with old Radeon card"
date: 2007-11-10
forum: Desktop Effects &amp; Customization
---

### Post by doggiedoll on 2007-11-10
I tried browse driver list on ati.com.  I did found that every time I choose my laptop VGA mobility Radeon 9200. ATI points me to 8.28.8. Only any cards that is newer than 9500 that ATI will points to new 8.42.3. I guess this is why I cannot setup my gutsy to use fglrx with aiglx.

Are there any of our friends can use this famous fglrx with old cards?

:(

---

### Post by lotu on 2007-11-11
Unfortunately ATI doesn't appear to have any plans to start support the older cards for linux.  However, there are some open source drivers that work very well for these cards.  I believe you need to install the xserver-xorg-video-ati package, using Synaptic.  However I also think that in Gutsy there is a bug in this package that prevents it from working, even though it worked fine with Feisty.  
In summery you can't use fglrx :( but you can use xserver-xorg-video-ati :) but it might be broken in Gutsy :(  hopefully someone will fix it soon :).

---

### Post by Ub1476 on 2007-11-11
The older ATI cards already have good support. For the latest, ATI has already released a driver which support AIGXL. ATI will also go open-source with their drivers soon.

---

### Post by Forlong on 2007-11-11
> **doggiedoll said:**
> Are there any of our friends can use this famous fglrx with old cards?
Famous? You mean Infamous.

I'll be happy the day the open radeon driver fully supports my Radeon 9600 XT.

---

### Post by qamelian on 2007-11-11
> **doggiedoll said:**
> Are there any of our friends can use this famous fglrx with old cards?

:(
Most older cards don't need the fglrx drivers. My laptop has a Mobility Radeon 9000 IGP and it works perfectly with AIGLX and the open-source ati / radeon driver that installs by default. In contrast, the fglrx drivers never worked right even when my card was still supported!

---

### Post by doggiedoll on 2007-11-12
My card is not so old. It is a sony vaio s260 with Mobility Radeon 9200 which is only two years. Not old for me. 

About the opensource driver. I did not have luck with GUTSY. It keeps stick to vesa. If I force xorg.conf. I will get the black screen. May be I have to try more, but I will have exam soon. Are there any of you have the same problem. Luckily I have Feisty on other partition.

Hehe, about the (in)famous fglrx, I used it on my workstation with x1900. It does perform a great job.. So sad, I cannot do the same on my laptop.

---

