---
title: "SDHC Card Window pops up after Standby on Dell Mini9"
date: 2009-07-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vickoxy on 2009-07-27
Hi, i just bought 16 GB SDHC Card and it didn´t work out of the box. Found fix here:

[http://www.mydellmini.com/forum/dell-mini-9-hardware-issues-problems/6365-sdhc-card-problem-after-upgrading-jaunty-9-04-a.html](http://www.mydellmini.com/forum/dell-mini-9-hardware-issues-problems/6365-sdhc-card-problem-after-upgrading-jaunty-9-04-a.html)

[http://filthypants.blogspot.com/2009/03/ubuntu-904-jaunty-jackalope-on-acer.html](http://filthypants.blogspot.com/2009/03/ubuntu-904-jaunty-jackalope-on-acer.html)

BUT, after standby it pops up window with SDHC. Can i disable it?

Thanks

Only to confirm-this happens only after Standby, not after reboot.

---

### Post by vickoxy on 2009-07-27
Found many users have same problem. Here is one workaround maybe, but i do not know where to find this media identifier:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271428](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271428)

> This also happens with audio CDs in Jaunty, kernel 2.6.28-13, on a Dell Inspiron 1520. Another (better?) option for behavior is store a media identifier on suspend, so that the medium is mounted back but no dialog will be shown if it hasn't been changed

Can someone explain me what does it do... and how?

---

### Post by vickoxy on 2009-07-28
Bump

---

### Post by vickoxy on 2009-07-28
If i add only: > options sdhci debug_quirks=1 in > /etc/modprobe.d/options, SDHC Card is recognized. But problem with Pop Up Nautilus Window after standby remains. 

Anyone Any idea

I mean, is there any option to dissable this pop ups (have no such problem with other sdhc cards... (of course, this is A-data 16 GB SDHC Card)

---

### Post by vickoxy on 2009-07-28
Yes-one thing more: old card were mounted to /home/media/, and this one is mounted to /home/sd....

---

### Post by vickoxy on 2009-07-28
SOLVED (partially): just uncheck media automount open (see picture).

---

### Post by vickoxy on 2009-08-01
My Kernel is 2.6.28.14-generic. I read that some have 2.6.30-and some are reporting that the situation with sd card is better. How/when can i expect this new kernel/how to get it?

Or it is too risky for as me newbie to rush the things?

---

