---
title: "XPS M1330 and Broadcom BCM4328 rev.3 Incompatibility."
date: 2008-04-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by avpap on 2008-04-26
I've read a dozen reports, articles, how to etc. on how to make my BCM4328 wireless card to work on Hardy but still nothing! It's a big disappointment to buy a Ubuntu "friendly" laptop with no linux driver for it's wireless card. I' ve tried ndiswrapper with no success and i'm frustrated. Please can someone with the specific laptop (XPS M1330) and the wirelless card (BCM4328 rev.3) write a "noob" guide on how to make this thing work? Please help, i hate going back to Vista again...Thanks!

---

### Post by maraja on 2008-04-26
Hi,

please consider to install Ubuntu 7.10, I used the official Dell restore DVD (available here):
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10#Dell_OS_Reinstallation_7.10_DVD_ISO](http://linux.dell.com/wiki/index.php/Ubuntu_7.10#Dell_OS_Reinstallation_7.10_DVD_ISO)

I usually wait some time before upgrading to a newer version, just to see what problmes other are facing ;)

If you follow these instructions:
[https://wiki.ubuntu.com/ThinkFinger](https://wiki.ubuntu.com/ThinkFinger)

you will also be able to use the finger reader to access; it is very useful when sudoing commands!

have fun with your xps

---

### Post by avpap on 2008-04-27
Thank you for the quick reply my friend. The Dell XPS M1330 is an amazing laptop and i definitely want to run it with Ubuntu. 
Ok I manage to setup up the wireless through ndiswrapper. For the first time i can see the wirelless blue led open and connect to internet but...after i restart my PC i can't connect to internet. I must reconfigure through manual configuration the wireless card and then I have internet again. What do you think is the problem. Does anybody know.

---

### Post by coachwhip on 2008-04-27
Are you using the right files with ndiswrapper ?

I ask this as I had a nightmare getting it to work but it turns out you need to find exactly the right files.

Although I use the bcmwl5.inf file i have to use another different firmware file as well. I think it was bcmwl564.sys file, if you are still stuck then I can try to find out which one it was by deleting my drivers and trying to put them back as I know I have the right one somewhere, trouble is I have probably every broadcom driver saved on my system just in case.

The other thing is that 7.10 used to report my chip as 4328 while it was actually a 4321ag chip, i don't think it matters but you may get luck searching for that number as well.

My laptop is a HP DV9646em but the wireless is a plug in card hidden inside it.

If you can't find the drivers then pm me with your email and I will send you some of mine to try.

Good luck.

Mike

---

### Post by avpap on 2008-04-27
> **coachwhip said:**
> Are you using the right files with ndiswrapper ?

I ask this as I had a nightmare getting it to work but it turns out you need to find exactly the right files.

Although I use the bcmwl5.inf file i have to use another different firmware file as well. I think it was bcmwl564.sys file, if you are still stuck then I can try to find out which one it was by deleting my drivers and trying to put them back as I know I have the right one somewhere, trouble is I have probably every broadcom driver saved on my system just in case.

The other thing is that 7.10 used to report my chip as 4328 while it was actually a 4321ag chip, i don't think it matters but you may get luck searching for that number as well.

My laptop is a HP DV9646em but the wireless is a plug in card hidden inside it.

If you can't find the drivers then pm me with your email and I will send you some of mine to try.

Good luck.

Mike

I'm actually using the "bcmwl5.inf" driver successfully and my only problem is that when i load Ubuntu I must reconfigure the wirelless card through network manager to have Internet. To tell you the truth i'm afraid to use another drivers because it took me 9hrs to find solution.

---

### Post by maraja on 2008-05-05
> **avpap said:**
> I must reconfigure through manual configuration the wireless card and then I have internet again. What do you think is the problem. Does anybody know.

maybe you need to let the system load ndiswrapper automatically at startup?

please see "7. Set the ndiswrapper module to automatically load at boot":
[http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper](http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper)

---

### Post by tbksandeep on 2008-09-09
Thank you very much for posting reply here. I was stuck with the BCM4328. Now Dell has its own iso for 8.04.1 at [http://linux.dell.com/files/ubuntu/hardy/iso-images/](http://linux.dell.com/files/ubuntu/hardy/iso-images/)

please download the image and burn it and install it. Since it belongs to dell, all the laptops which have dell with hardware will have these installed and work like charm.

You guys are awesome.

---

### Post by dizcrypt on 2008-09-10
Hardy includes a driver for BCM4328. There is a topic regarding this somewhere...

The only trick to get it is to enable 'hardy-proposed' updates in 'Software Sources'.

---

