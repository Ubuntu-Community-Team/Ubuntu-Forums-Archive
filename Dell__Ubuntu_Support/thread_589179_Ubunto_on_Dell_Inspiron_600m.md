---
title: "Ubunto on Dell Inspiron 600m"
date: 2007-10-23
forum: Dell  Ubuntu Support
---

### Post by yisongxie on 2007-10-23
Quite interested in the latest Ubuntu. Thinking to install on my Dell Inspiron 600M, after researching the topics in the forum, start to worry about the graphic card in Dell 600m.

I downloaded the latest ATI driver for Mobility Radeon 9000.

Also there is another stupid question as a new starter in Ubuntu. To install the Ubuntu, is it possible to keep some partitions from existing Windows? I have multiple partitions, and just want to use the C: for Ubuntu. Can I keep the others for data? 

Thank you.

---

### Post by Ek0nomik on 2007-10-24
> **yisongxie said:**
> Quite interested in the latest Ubuntu. Thinking to install on my Dell Inspiron 600M, after researching the topics in the forum, start to worry about the graphic card in Dell 600m.

I downloaded the latest ATI driver for Mobility Radeon 9000.

Also there is another stupid question as a new starter in Ubuntu. To install the Ubuntu, is it possible to keep some partitions from existing Windows? I have multiple partitions, and just want to use the C: for Ubuntu. Can I keep the others for data? 

Thank you.

You can keep any partition you wish.  Just make sure you know which partition is which before you delete on.  You should be able to read/write to your NTFS (Windows) partition out of the box with Ubuntu 7.10.

What are the specs of your laptop?  You could probably use Ubuntu, but if not you could use Xubuntu which is quite nice anyways.

---

### Post by yisongxie on 2007-10-24
Thanks for the reply. My Laptop is Dell Inspiron 600m. I tried the Ubuntu Live CD. It picked up most of the hardware, run fine. 

But I think I would need to modify the IPV6 setting and may need to install the ATI Mobility Radeon 9000 graphic card driver for Linux.

The display is ok but just could not enable the Compiz. But from the forum, it seems that the Compiz has some problems with the ATI card. Is there any suggestion?

---

### Post by bluedragon436 on 2007-10-24
You will have no real problem running the new Ubuntu on your 600m....  I had the 600m prior to getting my current D610 and it ran just fine.  I mean  you are going to have a few small tweaks to work out, but u can find all of those answers and fixes right here in these forums.  I had no problem setting mine up and getting it running perfect within the first few days...with the exception of playing DVD's but hey at least I can use my laptop and it enjoy it way better now that I am learning it a bit more than I did running windows....after all the small tweaks are worked out it is alot smoother and faster running in my opinion...

---

### Post by yisongxie on 2007-10-25
Thanks for the reply.

Have you got the Wireless Connection? I got Intel Wireless card.

---

### Post by JPJ007 on 2007-10-25
> **yisongxie said:**
> Thanks for the reply.

Have you got the Wireless Connection? I got Intel Wireless card.

I have the 600m and Intel wireless card.  It picked up the card and worked flawlessly, Right after booting up for the first time, I just clicked the networking icon in the top right and it showed my network already, I put in the key, and off I went.

That was actually just an hour or so ago. This is my first real Linux install, and so far I'm liking it.

---

### Post by bluedragon436 on 2007-10-26
I also had no problem with it picking up my Intel Wireless card after a restart.  I also did exactly as stated above, and it worked just fine....

---

### Post by yisongxie on 2007-10-27
glad to see you guys got wireless running on your dell. But after checking the system, ifconfig, I can see Ubuntu found my wireless card. But somehow in interfaces file, there is only wired eth0.

What else do i need to look at? DSL router? Do I need to reconfigure it? It runs fine with the WinXP on my laptop. 

Thank you.

---

### Post by yisongxie on 2007-10-27
Well after checking the ifconfig and networking and the DSL router, i found that 

1) in ifconfig, the wireless card eth1 did not get the IP from the router, which should be 10.1.1.3.

2) in network setting, i disable the roaming mode. And select using DHCP.

3) in router, i did not set the security, but i found in network setting, by default it is WPA Personal.

Base on these, anything I need to change? If i tried to set the security in router, but no idea which server i should use.

---

