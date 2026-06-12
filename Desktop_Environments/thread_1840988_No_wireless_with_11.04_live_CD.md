---
title: "No wireless with 11.04 live CD"
date: 2011-09-08
forum: Desktop Environments
---

### Post by Old *ix Geek on 2011-09-08
I burned a CD with 11.04 in anticipation of receiving my new laptop. I'm happily running 10.10 on all my other computers, but thought with the new one I'd go ahead and install 11.04 when it arrives [and I wipe windoze off its drive]. Afterward I fired up my current laptop from the live CD just to see what 11.04 looked like. To my amazement wireless did not work. I did all the usual things but to no avail; it simply did not see any wireless networks when I scanned, and even putting my network's name and passphrase in manually didn't work.

I had been thinking about doing the version upgrade to 11.04 on my current laptop, but now I'm not so sure. Just to be clear, my current laptop is a 4-1/2 year old HP dv6000, and has had multiple versions of Kubuntu on it; originally, I had to use ndiswrapper to get its Broadcom 43xx wireless card to work, but more recent versions of Kubuntu have made that unnecessary. So I expected 11.04 to be a piece of cake...but instead, I was SOL!

Does anyone have any thoughts on this? I don't want to upgrade to 11.04 only to find that it's not going to work with my wireless network. Well, I suppose I could go back to doing the ndiswrapper thing, but why should I have to?! Each version is supposed to get better, not be several steps backwards.

---

### Post by bkratz on 2011-09-08
Here is another active  11.04 Kubuntu thread about the same DV6 (I guess since it is just called DV6). Perhaps you can help each other.

[http://ubuntuforums.org/showthread.php?t=1840555](http://ubuntuforums.org/showthread.php?t=1840555)


I just noticed that he has a different wireless card if yours is a Broadcom device.

---

### Post by bkratz on 2011-09-08
Now I notice that you have specified BCM4311 in your opening line. Here is a really good page.

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

---

### Post by Old *ix Geek on 2011-09-08
Thanks for the links, bkratz. I'm just really surprised that 11.04 seems to have taken a few steps back in terms of its wireless support. I wasn't expecting that!

---

### Post by tom.tom_j on 2011-09-08
Hi Old *ix Geek,

                       Ya you were right there seems to be some problem with the Kernel Update with respect to the Broadcom Wireless driver :cry:. But just by Deactivating the Broadcom STA wireless driver from Additional Drivers menu seems to rectify the wireless driver issue in Ubuntu 11.04 :guitar:


Regards

---

### Post by bkratz on 2011-09-09
> **Old *ix Geek said:**
> Thanks for the links, bkratz. I'm just really surprised that 11.04 seems to have taken a few steps back in terms of its wireless support. I wasn't expecting that!



I trust it took care of you, if not post back.

---

