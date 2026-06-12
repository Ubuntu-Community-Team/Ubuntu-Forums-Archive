---
title: "LXDE CPU Usage Monitor"
date: 2010-11-14
forum: Desktop Environments
---

### Post by edwardp on 2010-11-14
I have installed the LXDE desktop on my ubuntu (xubuntu) 10.04.1 LTS installation.

By default, it displays the LXDE CPU Usage Monitor at the bottom.  Does this monitor actually use CPU resources itself, and if so, would it be recommended to remove it from the panel on a slower system?

This is on an AMD K6-2 system (500 MHz) with 640Mb of PC-100 memory (circa 2001).  By itself, the system is better than average when using LXDE, but I have noticed that when the system is checking for updates or when it is printing something, the usage monitor essentially displays 100% CPU usage until the updater or printer finishes, as the case may be.  It will also indicate 100% usage when the web browser is loading in a web page.

Thanks in advance for any advice.

---

### Post by 3Miro on 2010-11-14
AMD K6-2: I believe in Egypt they were using those to compute the dimensions of the Pyramids, when they were building them. Your RAM is a healthy amount, so this is helping you a lot.

Anything and everything on your system takes CPU time, sometimes more sometimes less. On a modern CPU, most of the processes will not be noticeable, however, on such an old CPU everything can make a difference. The CPU monitor shouldn't take much, but still, you can try without it to see if it helps.

Depending on the web-page that I visit, I can see short spike to 100% on my CPU (Phenom II X4, basically K10). So what you are saying is normal. Checking for updates is also heavy, you may want to stop the system from doing it automatically so you can do it manually yourself only when it doesn't bother your other work.

---

### Post by edwardp on 2010-11-14
Thanks.  I have now removed it from the panel.  

What I will do is test this against sites that use a lot of Flash ads and see what happens.

---

### Post by 3Miro on 2010-11-14
> **edwardp said:**
> Thanks.  I have now removed it from the panel.  

What I will do is test this against sites that use a lot of Flash ads and see what happens.

You should probably install Flashblock for Firefox (they also have it for Chromium). This will allow only flash apps that you explicitly give permission to run. Flashblock will help you way more than removing the CPU monitor applet.

---

### Post by edwardp on 2010-11-14
I currently do not use Flashblock, but Flash 10.1 does not work with the K6-2 processor.  10.1 contains the CMOV instruction which is not supported by the K6-2 (CMOV came into existence well after the K6-2 did.) and that causes a Flash crash on systems with this CPU, so I have to continue to use Flash 10.0 until this is fixed.

Bug reports have been filed with both Mozilla and Adobe, but as of now, neither has been resolved.

---

### Post by 3Miro on 2010-11-14
Flashblock supports all versions of flash. Give it a try. As for the bug, Mozilla cannot do anything, since Flash is close source and controlled by Adobe. I wouldn't hold my breath for Adobe to care about Linux, look at how long it took them to get reasonable 64-bit Flash support.

---

### Post by edwardp on 2010-11-14
On my 64-bit desktop (running 64-bit xubuntu), I am using the 64-bit beta of the Flash plugin that was made available, that works.  :)

The CMOV Flash crash also affected Windows as well, so I hope Adobe will find a solution.  The K6-2 is dual-boot with WinXP.

---

