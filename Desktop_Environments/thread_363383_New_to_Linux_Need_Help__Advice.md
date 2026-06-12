---
title: "New to Linux: Need Help / Advice"
date: 2007-02-16
forum: Desktop Environments
---

### Post by Bashed on 2007-02-16
I'm new to desktop linux and need help deciding what distro to use. I attempted to install Ubuntu and Kubuntu (this was a mess) but Ubuntu was ok. 

**This is my situation:**
- using Vista Ultimate (love it)
- using Office 2007 (love it, aside Outlook slowness bug)

**My requirements:**
- fancy desktop
- bundled software
- ease of use (like Windows Explorer is easy to use, unlike "apt get")
- stability (important!)
- ability to run *any* Windows software such as Office 2007
- multimedia minded would be nice

What software do I download / install to be able to run Windows software? 

**Another issue in regards to 'easy of use'**
- during kubuntu testing yesterday, I downloaded firefox.  I had no idea whatsoever HOW to install this!  In Windows, you just double click and it begins. In Kubuntu/linux, I double click and it extracts. Then there was nothing to from there! What am I missing here?

What do you think of these? 

Linspire (commercial???)
Freespire
OpenSuse
Gentoo
Alinux

Is there any place/site I can see comparisons, screenshots and quality/performance ratings?

Thank you.

---

### Post by pay on 2007-02-16
Linux is *not* Windows. It runs things abit differently. To install software you need to use apt-get, aptitude or synaptic (adept for kubuntu). You can run *some *Windows software with Wine, Crossover Office or Cedega. If all you want to do with Linux is run Windows software, then maybe Linux isn't for you. You could also install Windows into vmware, qemu or virtualbox. For a fancy desktop look at Beryl and compiz. Linux is stable. You will get used to apt-get and then realise how superior it is compared to Windows Explorer. To install firefox type ```
sudo aptitude install firefox
```or search for firefox in synaptic. Even though Ubuntu has Firefox installed as default (kubuntu does not)

Good luck.

---

### Post by Bashed on 2007-02-16
What about my other questions? Please help

How do I install firefox for example?
How do I install wine?

---

### Post by Sklasko on 2007-02-16
If you "love" Vista so much, might I ask why you want to make the move to Linux? That being said, I wouldn't expect the exact same experience your getting in Vista.

Firefox is in the repos, and so is WINE.

---

### Post by rsambuca on 2007-02-16
Firefox comes pre-installed with both ubuntu and kubuntu.

---

### Post by Bashed on 2007-02-16
I like linux too (played around with it a few times including kde/ubuntu) but I want to possibly go fully linux eventually if the performance and stability, along with security is better than Vista.  

Please see my first post, I edited it (about linux distros)

---

### Post by pay on 2007-02-16
[URL="http://monkeyblog.org/ubuntu/installing.html"]Howto install anything in Ubuntu
[Distro Watch](www.distrowatch.org)
[/URL]

---

### Post by Bashed on 2007-02-16
Thanks, I was already aware of distrowatch and that's where I got the list of o/s I mentioned before. 

A few more questions please:

- what is the overall advantages of linux over Windows (Vista)?
- in comparison to Windows, how does Ubuntu for example compare with stability and performance (speed)?

---

### Post by pay on 2007-02-16
Well it's kinda hard to test them out for speed because I can't think of a benchmarking program that works on both Windows and Linux. But personally, I think that Linux performs better because it is less bloated and you don't get spyware which hinders  the performance. Dapper is very stable and Edgy has bleeding edge software but I find that Edgy is very stable aswell but it might have a few more bugs, though it is pretty mature now. If you want the most stable distro look at freebsd, debian sarge and slackware.

---

### Post by Bashed on 2007-02-16
Thanks.  I just tried freespire....horrible. Took 5 minutes to boot (hd install, not live) and interface is generic, low quality. 

Can someone tell me the *SAFE* way to remove freespire from my 30GB partition? I selected "write mbr" during the install, so I don't want to mess up the MBR and get locked out of Vista.

---

### Post by rsambuca on 2007-02-17
I am kinda confused.  Do you have Vista, Freespire, and Kubuntu installed?  If so, what is the last linux distro that you installed.  It is likely that one which grub is using for boot up instructions.

---

### Post by kamaboko on 2007-02-17
For what it's worth...I'm absolutely thrilled with Ubuntu.  My background is in IT design and implementation of MS networks.  This is my first go with Linux and I'm sold on it.  The break came with Vista.  There's no sound reason (other than maybe gaming) why someone should need a duo core processor, more than 2GB of ram, and a 256MB video card just to run a bloody OS at optimal levels.  I threw Ubuntu on a Compaq Presario that runs an AMD Sempron at 1.6GHz, 512MB, a 40GB hard drive and a ATI Express 200M vid card.  It blows the hell out of its former configuration of XP.  For instance, last night I ran a movie, watched streaming video, chatted and had a number of other apps open.  This would have crushed the little lappie with XP.  With Ubuntu it didn't even take a hit.  THAT'S HOW IT SHOULD BE.  Moreover, I can trick it out to no end way beyond anything Vista can do.  All that for FREE??!?!  Granted, I'm new at this...day 2...but I'm certainly sold on this product.

---

### Post by darklyndsea on 2007-02-17
> what is the overall advantages of linux over Windows (Vista)?
You may want to check out [http://www.whylinuxisbetter.net/]("http://www.whylinuxisbetter.net/").

---

### Post by Bashed on 2007-02-17
> **rsambuca said:**
> I am kinda confused.  Do you have Vista, Freespire, and Kubuntu installed?  If so, what is the last linux distro that you installed.  It is likely that one which grub is using for boot up instructions.


Please read my first post carefully
> 
This is my situation:
- using Vista Ultimate (love it)

I tried freespire (did not like it at all). I've tried Kubuntu Edgy and Dapper, it had some issues for whatever reason.  I am going to try Ubuntu once again now and test the waters. 

Anyone suggest a theme for Ubuntu that looks like Vista at least? I cannot switch that easily over LOL.

---

### Post by rsambuca on 2007-02-17
Yes I read your first post.  I am also trying to help you, but again you did not answer the question.  What Operating Systems do you currently have on your hard drive?  You can "use" many of these different OS's without actually installing them.  So, in order for us to give you the proper advice or instructions on how to remove Freespire from you Hard Drive, we need to no the current set-up.

---

