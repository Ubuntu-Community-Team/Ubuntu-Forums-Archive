---
title: "Brother MFC7440"
date: 2010-04-12
forum: Desktop Environments
---

### Post by jimw on 2010-04-12
Just yesterday, I bought a Brother Multifunction 7440.

Before I bought it, I made sure that there were ubuntu drivers for it.

I got it all hooked up, and after several tries at installing the drivers properly, I was no further ahead.

This evening, I went through process in the How-To posted on October 25, 2007. At the end of it I was able to print an Ubuntu test page successfully, then nothing.  After some more fooling around, including a reboot of the machine, I was able to print another test page, and nothing more since.

Does anybody have any good advice for me?

Thanks,

JimW

---

### Post by jimw on 2010-04-12
> **jimw said:**
> Just yesterday, I bought a Brother Multifunction 7440.

Before I bought it, I made sure that there were ubuntu drivers for it.

I got it all hooked up, and after several tries at installing the drivers properly, I was no further ahead.

This evening, I went through process in the How-To posted on October 25, 2007. At the end of it I was able to print an Ubuntu test page successfully, then nothing.  After some more fooling around, including a reboot of the machine, I was able to print another test page, and nothing more since.

Does anybody have any good advice for me?

Thanks,

JimW

I've just discovered that I can print as long as I go through cups.  Going through lpr won't work at all.

JimW

---

### Post by BJ_Covert_Action on 2010-04-12
Only slightly related, but I was trying to do something more complicated involving a Brother MFC-9440CN and a linksys printserver about a month ago. However, while working with that setup, I had a similar problem where I was getting a good print once and then locking up the printer so that I would have to reboot everything to get it to work again. The interesting thing was that I was connecting to the printer/server from multiple machines and one print job from my ubuntu box would prevent any of the other computers from printing out to the printer as well.

After doing some digging I found out that sometimes, with the Brother printers, there can be problems with printer queues. Essentially, printing one kind of job can clog up the printer queue and prevent any other jobs from going until the whole system is rebooted. There was a workaround that prevented that, I found, that involved editing the URI of the printer through the web interface for CUPS: [http://localhost:631](http://localhost:631) .

I can't find the posts that I read regarding that particular problem, but I may have linked to them when I was posting on here about my own problems back then in [This Thread.](http://ubuntuforums.org/showthread.php?t=1384086) You might try poking through there and seeing if any of the stuff I discussed or linked to in it could help you. If not, then this post was probably a waste of your time. You might also try doing some Google searches for something about Brother MFC printers and blocking, clogging, or holding up the print queue. 

I know that's not a lot of information, but it reminded me of what I was running into so I figured I would respond just in case it helps. Also, just so you know, I never did get my own setup working but that's because I got sidetracked and never got a chance to keep trying to work on it. So, yeah.

I hope this helps.

Cheers.

---

