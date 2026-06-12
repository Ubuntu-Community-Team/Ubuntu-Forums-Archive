---
title: "Which Dell?  Inspiron 1501 or  E1505N"
date: 2007-06-15
forum: Dell  Ubuntu Support
---

### Post by nicedream on 2007-06-15
Hello all...

A little background on me.  I've been using Linux off and on for about 10 years.  I started with RedHat 5.0 (the original, not RHEL) because it was the first distribution to support my 2MB Matrox video card :)  I used one distro or another as my sole desktop OS until about 2003 when I switched to XP.  

Now that Ubuntu is getting quite popular, and Dell came out with pre-installed options, I decided to get a new laptop and run Ubuntu on it.  System76 looked good, but Dell just gives you more for your money, so I will probably go with them.

However, I was fishing around the Dell site and found the 1501....a low end laptop that's only $499, and has better specs than the E1505N which has Ubuntu pre-installed.  Looking over this site and tuxmobil, it seems that quite a few people are running Linux on the 1501.  Since I am not a Linux newbie, I was thinking I could make out better buy buying the cheaper 1501 and installing the latest version of Ubuntu (7.04?) myself.

So does anyone have any suggestions on why I should not do this?  I am not scared of configuring things, editing files, using the command line, etc.  Of course anything working out of the box would be nice.  Am I missing any problems between ubuntu and this laptop that anyone can warn me about?  (Sound, Suspend/Hibernate, Function buttons that don't work, etc)

Thanks in advance....

---

### Post by abburdlen on 2007-06-16
I can't speak to the idea of loading Linux on it but my wife has the 1501 (though still running windows :rolleyes:) and it's a great machine.
Besides the intel vs AMD the only difference between the machines is the 1501 doesn't have the media buttons up front nor does it have firewire like the 1505 does.

---

### Post by vco08 on 2007-06-16
I actually use the Inspiron 6400 and im running Kubuntu on it. Its running great so far. Just had some minor headaches with the wireless, but got that taken care of.

---

### Post by redDEADresolve on 2007-06-16
Hi I run a blog about running Ubuntu on the Dell 1501, its a great experience and I love my 1501 very much. But it does have a few warts that the Dell 1505n won't. The wifi doesn't work out of the box, the two fixes are pretty easy and native Linux drivers are being developed for it. Second ATI Linux drivers are awful when compared to Nvidia or Intel Linux graphic card drivers. So using Beryl is functional but not great. 

Getting a 1501 will require you to use the command line and install some stuff to get everything to work. Check out my blog if you want to learn more about running Ubuntu on the 1501, [www.ubuntu1501.blogspot.com](www.ubuntu1501.blogspot.com)

If I had to choose, I'd go with the Dell 1505n with the Intel 950 graphic card.

---

### Post by nicedream on 2007-06-16
Hi RedDead...I spent all last night reading your blog before I posted to this board.  Let me say: GREAT resource!

Thanks for your reply here.  I am certainly not afraid of running a few commands to get the wifi working.  I am not a Linux n00b.  As for the graphics card, I don't plan on running any 3d window managers, so as long as it looks decent for basic web browsing, etc, I am happy.

Aside from these two issues, are there any other reasons you would not get the 1501?  How well does the sound, hibernate/suspend, etc work?

---

### Post by jaybuntu on 2007-06-16
In general, I would stay away from the 1501 line and go for a 1505 just because the 1505 is a higher grade machine that I suspect performs better due to better quality components (much like the old Inspiron 8600 would outperform a 2600 with equivalent specs).  I don't have a 1501, but I do have a 1505N and EVERYTHING just worked out fo the box, wireless, suspend, hibernate, firewire, etc.  I would definitely recommend it for the relatively little increase in cost.

---

### Post by neptho on 2007-06-17
I love my 6400.  It's bulky, it's enormous, and it has the X1300 video, but I *still* wouldn't trade it!

---

### Post by nicedream on 2007-06-18
Well here is what I ended up doing....

After poking around the Dell outlet site I found a refurb 640M that came with the same wireless NIC and video card as the E1505N.  So essentially, its almost the same machine but with a 14 inch screen, which is really my preferred size for laptops anyways.

I plan on doing a write up on the install, to add to all the others on tuxmobil.org.

---

### Post by Denny Johnson on 2007-06-30
a

---

### Post by redDEADresolve on 2007-07-02
nicedream yeah suspend and hibernate only work if you are using the 1.7 bios. Pretty easy to flash back to 1.7

---

### Post by Unicast on 2007-07-02
> **redDEADresolve said:**
> nicedream yeah suspend and hibernate only work if you are using the 1.7 bios. Pretty easy to flash back to 1.7
I find that hibernate and suspend work just fine using [bios version 2.3 on the 1501.](http://support.euro.dell.com/support/downloads/download.aspx?c=uk&l=en&s=gen&releaseid=R151827&SystemID=INS_PNT_1501&servicetag=&os=WW1&osl=en&deviceid=13120&devlib=0&typecnt=0&vercnt=5&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=202052)

---

