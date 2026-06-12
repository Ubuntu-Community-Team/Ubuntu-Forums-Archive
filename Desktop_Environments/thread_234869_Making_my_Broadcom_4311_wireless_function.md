---
title: "Making my Broadcom 4311 wireless function?"
date: 2006-08-12
forum: Desktop Environments
---

### Post by Wej on 2006-08-12
I just got a nice shiny new core duo dell with the broadcom 4311 wireless card in it, according to lspci. Well, it just knows it's Broadcom and 4311. It doesn't know it's a wireless card. It says "unknown device." Anyway, I went through the steps [here](http://www.ubuntuforums.org/showthread.php?t=185174) 3 times and it never shows the wireless card in the network manager applet. It shows the hardwired ethernet connection, and lo, which I am guessing is the loopback interface. But it doesn't show the wireless. I've tried using the .o file available as well as downloading the driver from dell and extracting it and using the ndisgtk driver installer that asked for the .inf file. That was a no-go too. :( I am liking ubuntu but I would like to get my wireless card working properly. Does anyone have experience with this exact broadcom chip and ubuntu?

The exact result from lspci is:
*0000:0c:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)*

Any insight will be appreciated greatly. :)

---

### Post by haiku99 on 2006-08-15
I had similar problems w/ a Broadcom 4311 in an HP nx6310, tried a few fixes I found here but had the same result, but then tried the ndiswrapper installation procedure at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
and that did the trick, looks like having the latest version is essential, I finally figured that out after reading fixes for similar problems w/ Suse .   FWIW i used drivers I copied from my windows partition.  Also, AFAIK the blacklist step shown to disable the builtin Ubuntu driver shown in many Broadcom posts is not required for the 4311 as the driver does not recognize it anyway...

---

### Post by acrossbetween on 2006-08-17
i just got done using  [this]("http://www.ubuntuforums.org/showthread.php?t=193350") guide and it worked perfectly for my dell e1505 which has the broadcom 4311 wireless card.

I installed network manager after that and they work fine together. I did pull the drivers from the windows partition too and that worked fine, it was pretty easy and I ve been trying a while to get it working! I hope this helps!

---

### Post by snpz on 2006-09-05
With ndiswrapper my nx6310 with Broadcom 4311 works perfect!;)

---

