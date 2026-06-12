---
title: "Disappearing icons in nautilus and pcmanFM (ubuntu and lubuntu)"
date: 2012-12-30
forum: Desktop Environments
---

### Post by fivestones on 2012-12-30
Running Ubuntu 12.10: I was having problems in nautilus with disappearing icons, some file/directory icons were visible and others would not be visible, clicking on icons or moving the mouse over them would change which were visible and which were not (others would disappear and some of the disappeared ones would become visible). I installed lubuntu on top, and booting into lubuntu I had the same problem in pcmanFM. I then did a reinstall from scratch, erasing my hard drive and installing fresh lubuntu 12.10, and after it finished installing I still have the same problem. What's going on?
I did md5 checksum on the lubuntu iso which I downloaded yesterday, which was good, and I did "check disc for errors" before I installed with it, and no errors were found. How could a fresh install end up with the same problem?
I tried searching for this but didn't really find anything with the terms I could think of to search with.
Thanks everyone for your help!

---

### Post by vasa1 on 2012-12-30
When you say you erased your hard drive, does that mean you start with a clean /home each time? Or are some files in /home synced by Ubuntu One or whatever?

---

### Post by fivestones on 2013-01-01
No, the hard drive was wiped, and there is nothing kept in /home. (Although there is a secondary hard drive in the computer which has personal files on it; however, I didn't make use of it at all when installing lubuntu so I don't think it would be the problem.)

I attached a few screen shots in case that helps anyone.

Thanks!

---

### Post by fivestones on 2013-01-04
I still haven't figured this one out, just wondering if maybe some kind soul would be willing to look at my screen shots to see if they know what the problem is. 

I did try the lubuntu disc on another computer and it worked flawlessly. Weird.

On the problem computer, I get the same problem having installed it to the hard drive or running the "try without installing" option from the cd.

---

### Post by fivestones on 2013-01-04
It gets weirder. I unplugged the two hard drives inside the computer. Then I booted from CD and did "try lubuntu without installing". It still has the same problem. I tried again on the other computer that worked just to make sure, and again, it works flawlessly with the same lubuntu CD. (Except, weirdly, in the 'good computer,' the screen is much darker than it should be. When booting windows, it's nice and bright. When booting lubuntu, it's like someone turned the brightness way down. Except that brightness is all the way up...so there's that, but no other problems.)

Back to the original problem: I would say it's something with the graphics card in the computer or something, except that movement of the mouse over the directory icons sometimes makes them appear or disappear. And selecting the empty space where the directory icons should be sometimes makes then appear. So if the mouse is that involved in making the icons appear and disappear, how could it be the graphics card?
Maybe a memory issue in that computer? 

Also, a couple of other things I noticed. Often when starting a program, e.g., chromium, upon closing it a message pops up saying that it encountered an error, asks me if I want to send in a report, and asks if I want to restart the program
Also, in the "start" menu, the little arrows pointing to the right where the submenus pop up are not displaying correctly--they behave a little like the directory icons, coming and going with mouse movements over them, sometimes staying when they shouldn't and sometimes not coming when they should.
Finally, I'm pretty sure that the colors are wrong in the bar showing a running program at the bottom of the screen. Look at my screen shots and you'll see what I mean.

Thanks every one

---

### Post by fivestones on 2013-01-05
More updates:

I unplugged the harddrives in the computer. I downloaded lubuntu 13.04 beta. I ran it from the CD. Still same problem. What gives?

I tried swapping out both memory chips in the computer in turn, but still no change. 

Anyone?

---

### Post by uzumakifahim on 2013-01-06
Have you use any ubuntu/lubuntu before? Not sure, but may be you are having problems with your graphics.

---

### Post by fivestones on 2013-01-06
I have used ubuntu 10.04 on this computer in the past without problems. I think the problem began when I upgraded to 12.10 (or maybe soon after I upgraded?)

---

### Post by uzumakifahim on 2013-01-06
You have tried Lubuntu 13.04 beta. What about 12.04? 12.04 is better than both 12.10 & 13.04 as it is LTS version. If you can please try 12.04 and post the output here.

---

### Post by fivestones on 2013-01-07
I'll try lubuntu 12.04 when I get home later...thanks for the suggestion!

---

### Post by fivestones on 2013-01-09
Ok, I just got a chance to try out lubuntu 12.04, and, WOAH, it works! There's no problem with icons. So it must not be my graphics, or memory, but a bug in versions of ubuntu after 12.04...right? I had the problem with ubuntu 12.10, lubuntu 12.10, lubuntu 13.04 beta, but not with lubuntu 12.04 (or with ubuntu 10.04) all on the same hardware.

What was it that changed in the way icons for files and directories are displayed (also, the arrows in the start menu pointing to the right for submenus) between 12.04 and 12.10? Maybe there is a known bug but I can't figure out what to search for to find it if it is. 

I'd love to be able to figure it out because though it's great to have things working in 12.04, I don't want to be stuck in this version forever.

Once again, thanks for your help everybody!

---

### Post by ethanay on 2013-02-06
fivestones is right, it's a bug.  We run a small computer refurbishing joint, and 12.10 is just really buggy with display issues.  We are experiencing the exact same problem.  

I'm worried that support for older graphics hardware is falling by the wayside after 12.04, even in projects like Lubuntu.

Can you help by filing a bug report against these versions of Ubuntu?  I will add to it once you get it started...

[https://help.ubuntu.com/community/ReportingBugs#How_to_report_bugs](https://help.ubuntu.com/community/ReportingBugs#How_to_report_bugs)

---

