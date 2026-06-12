---
title: "Help Building A HTPC/Steam/Ubuntu System"
date: 2015-01-23
forum: Gaming &amp; Leisure
---

### Post by snore2 on 2015-01-23
New here to these parts as well as linux as an OS so go easy on me. I didn't see any help building section. If this is in the wrong section I apologize in advanced. 
I did play a little bit around with Ubuntu 14 on the old PC listed below however it is old so just time to upgrade. Had blue screen errors when was running windows so more then likely hardware etc was starting to fail...but anyway here it goes.


Looking to build a HTPC that I can run Steam on. The OS I will be using Ubuntu 14. I have built a computer in the past but it is now 10 years old so it is outdated and not worth upgrading anymore in my opinion. Looking to get the most bang for my buck naturally. I will need an entirely new setup as the hardware in the old pc are dated (ddr, usb 2.0, ide hard drive, 512mb graphics card etc...you get the picture) Was thinking of going this route instead of getting a PS4 for now. I have a ps3 so I will not need a blu ray/dvd player drive. I do however have a DVD RW drive if the case does have a spot for one.


If possible I would like to be able to upgrade in the future, so would like to have expansion slot for a better graphics card down the road. Or is this a must for the initial build and no onboard graphics would be worth using for the purpose I am looking to use it as.


Would also like to use this possibly as a NAS, however don't plan on keeping the machine on 24/7 so not a full time NAS if that makes sense, with the plans in the (way) distant future to have a separate NAS instead.


Initial build only looking to start with 1 sata drive and then a SSD (for OS or would I not really need an SSD) 


So I am pretty much looking for suggestions for just about every aspect of this build. What type of HD should I be looking at WD red, green....


Looking for lower power consumption, quiet, etc...


Thanks for any help or guidance anyone can offer me with this build.

---

### Post by TheFu on 2015-01-23
Lots of websites have $500 gaming rig builds.  Pick one. Gaming is the heavy user of the stuff you're talking about.

HTPC is about the GPU drivers. If you get last year's nvidia middle-of-the-road card ($100-$150), drivers shouldn't be an issue. For an HTPC, a $20 nvidia or AMD or the built-in Intel GPU will be fine.

Being a NAS doesn't take much.  Just don't use wifi and put a GigE network into your house.  Of course, if you insist on using ZFS, then lots and lots of ECC RAM is needed. No other file system requires that.  If you do want a ZFS NAS, go over to the FreeNAS site and start reading. Those folks build dedicated NAS devices, so don't expect gaming performance.

Power and quiet are opposites.  The GPU will be the main reason to have a big PSU. Without a power-sucking GPU, 400W is fine. Get an 80% efficient or better PSU to reduce waste, heat, noise. Not much use in going higher on the efficiency.

I'm not a gamer ... none of my systems have more than 430W PSUs or a $20 GPU.  Looking at the power meter (built into the UPSes), shows none of them use more than 140W, even at boot.  One has 6-HDDs connected.  OTOH, none of my CPUs draws more than 95W either.  My HTPC player (not recorder), uses 26W and is completely silent.

Do you plan to record TV?  If so, highly, highly, highly, recommend a network-based tuner, not USB, not PCI-whatever cards. Network tuners provide flexibility and are easier to setup than the put-in-pc type of tuners.

---

