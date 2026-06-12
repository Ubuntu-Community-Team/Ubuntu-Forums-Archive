---
title: "Do I need to upgrade my kernel to run WoW on Cedega 4.3.1?"
date: 2005-04-13
forum: Gaming &amp; Leisure
---

### Post by Raven-sb on 2005-04-13
Hi All,

After reading several reviews on Cedega I decided to take the plunge, uninstall Windows and just run Ubuntu, using Cedega to run my windows games.

According to Cedega 4.3.1 release notes, 'There is ptrace bug in the 2.6.9 and 2.6.10 kernels that may cause copy protection to fail. At this point there is no known work around, and TransGaming recommends avoiding the use of these kernels at this time. This bug appears to be resolved in the 2.6.11 kernel.'

This has me a tad bit nervious as I really want to run WoW. I've read a number of other forum posts here from users who have installed WoW using Ubuntu but none of them mentioned having to upgrade their kernel to do so.

So my question is as per the thread heading, Do I need to upgrade my kernel to run WoW on Cedega 4.3.1?  If so, how do I do this and what version of the kernel do I need to download?  (I'm assuming I'd have to use the 2.6.11 kernel).  

Regards,

Raven

---

### Post by XDevHald on 2005-04-13
You can run 2.6.11 at your own risk, I will actually try to uninstall the 2.6.10 and run the 2.6.11, and that being said they might be conflicting each other which is why 2.6.11 might be freezing hard on everyones box when they try to use it.

   - To check on what others are talking aboutt on this topic: [http://ubuntuforums.org/archive/index.php/t-21258.html]("http://ubuntuforums.org/archive/index.php/t-21258.html")

**[color=black]/#Edit $[/color]**[color=black] Do NOT do this as I just tested this kernel *again* and removed the 686 header and it is still fighting with the 2.6.10-5 linux image, and of course this is the dmvlinuz main source of the boot, which is HUGE NO NO to do!
[/color]

---

### Post by Giawa on 2005-04-14
Copy protection in this case, I'm pretty sure, is allowing the program to access the CD-ROM drive to make sure you have the cd in to run the program. World of warcraft doesn't need any CD in the drive to work properly, so I think you should be fine. :-) By the way, World of warcraft works awesome once you get things set up. If you have any questions to get better frame rates, just look around here or post, lots of us play it and have had to go thru setting it up (me being one of them). Good luck! and welcome to Ubuntu :razz:

---

### Post by Raven-sb on 2005-04-14
Thanks Giawa,

I am happy to say that I got everything working without any problems whatsoever on a 2.6.10-686 kernel and the game runs like a dream. Transgaming the best $5.00 I've ever spent.

Hmm maybe we should start our own online guild so that all of us Ubuntu users could game together.  What server does everyone play on?

Regards,

Raven:-P

---

### Post by fng on 2005-04-14
shattered hands (EU PVP server) : Allaince

---

