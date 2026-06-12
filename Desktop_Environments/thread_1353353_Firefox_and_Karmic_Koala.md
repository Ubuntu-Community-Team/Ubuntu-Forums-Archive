---
title: "Firefox and Karmic Koala"
date: 2009-12-12
forum: Desktop Environments
---

### Post by coredeal on 2009-12-12
Hi everyone,

I have upgraded from Jaunty to Koala but I find it very strange that Firefox now literally crawls, compared to Jaunty Firefox. After doing quite a bit of troubleshooting as well as a lot of tweaking in Firefox about:config (pipelining etc.etc.) I find no improvement. A few figures : all site pages, in Jaunty Firefox (which is ver. 3.08) take no more than 3 to 5 secs to load. In Koala Firefox (ver. 3.5) the average loading time is 20 to 35 secs and over. And this includes links within the same site. I mean, it's unacceptable. I've even tried with Koala live disk, which permits using Firefox, but I get exactly the same results. I've tested my broadband connection with specific software, but I systematically get "excellent, 8000 kbit/sec). Has anyone who upgraded to Koala experienced the same problem with Firefox 3.5 that comes with the upgrade ? I'm curious to know whether I am the only one experiencing this problem or has anyone else found an appropriate solution. Thank you for your responses.

---

### Post by roggenschrotbrot on 2009-12-12
1. did you change your builds architecture? flash for me slowed down 64bit firefox so far that i had to revert to 32 bit.
2. is it possible you had disabled ipv6 before? if you don't know check the wiki for more info.
3. you could try swiftfox (firefox compiled for your architecture). it won't account for the loss of performance you mentioned, but in some cases it does change things for the better.

---

### Post by coffeecat on 2009-12-12
Is it possible you've been hit by this bug?

[https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757)

Karmic is OK for me, but quite a few people seem to have been affected. Post #7 in that Launchpad thread is interesting. Have you tried disabling IPv6 in Firefox? Have you tried the OpenDNS servers?

---

### Post by coredeal on 2009-12-13
> **coffeecat said:**
> Is it possible you've been hit by this bug?

[https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757)

Karmic is OK for me, but quite a few people seem to have been affected. Post #7 in that Launchpad thread is interesting. Have you tried disabling IPv6 in Firefox? Have you tried the OpenDNS servers?
Thank you Coffeecat. The link indicates that it is a DNS bug built within Koala. I think it is inexcusable that the Koala developers have not prioritized this bug as release critical, since it is a problem that affects not only Firefox but all other network applications. As a result, I have erased Koala and gone back - happily - to Jaunty, which is not affected by this problem. But my disappointment with the Ubuntu developers persists. I think they have done a big disservice to this excellent OS.

---

### Post by coredeal on 2009-12-13
> **coffeecat said:**
> Is it possible you've been hit by this bug?

[https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757)

Karmic is OK for me, but quite a few people seem to have been affected. Post #7 in that Launchpad thread is interesting. Have you tried disabling IPv6 in Firefox? Have you tried the OpenDNS servers?
Thank you for your response. It would appear that this is a DNS bug, compliment of Koala.

---

### Post by coredeal on 2009-12-13
Thank you for your response. It would appear that this is a DNS bug, compliment of Koala.

---

### Post by coffeecat on 2009-12-13
> **coredeal said:**
> I think it is inexcusable that the Koala developers have not prioritized this bug as release critical, since it is a problem that affects not only Firefox but all other network applications.

Excuse me? Inexcusable? Be very careful when being so very judgemental - judgements have a nasty habit of coming back to haunt one. This is a bug which affects a small minority of users, but I agree that it is a serious one. However, the problem is in the DNS resolver - i.e. the router - which just happens to get unmasked in Karmic. Upstream developers are responsible for fixing this - **not** Ubuntu developers - which is a bit unfair because the problem is not even within Linux/Ubuntu.

I have not been affected by this bug - or at least not with my everyday Linksys router. So when I first heard about it I was interested enough to try out no less than 4 other different makes of router. There was no problem with any of them. You'll see which are (some of) the problem makes in that thread.

By the way, is there an echo in here, :-s or are the duplicate posts something to do with delayed DNS resoluton? :wink:

---

### Post by coredeal on 2009-12-13
> **coffeecat said:**
> Excuse me? Inexcusable? Be very careful when being so very judgemental - judgements have a nasty habit of coming back to haunt one. This is a bug which affects a small minority of users, but I agree that it is a serious one. However, the problem is in the DNS resolver - i.e. the router - which just happens to get unmasked in Karmic. Upstream developers are responsible for fixing this - **not** Ubuntu developers - which is a bit unfair because the problem is not even within Linux/Ubuntu.

I have not been affected by this bug - or at least not with my everyday Linksys router. So when I first heard about it I was interested enough to try out no less than 4 other different makes of router. There was no problem with any of them. You'll see which are (some of) the problem makes in that thread.

By the way, is there an echo in here, :-s or are the duplicate posts something to do with delayed DNS resoluton? :wink:
Hi Coffeecat,

I agree with your concept of being prudent in judgment, but, please, take a look at how many people are complaining and the incredible efforts they have made to find a way around this problem or a solution. I'm talking about the link you mentioned to me. If I said "Ubuntu developers" I did not mean to offend anyone : mine was just a complaint directed at the people who have released this upgrade. It is up to them, I believe, to make sure that such an important aspect of the new version is fully functional. Hey, we're not talking about a minor program, we're talking about Internet connection, which is a prime tool for everyone. "Upstream developers"...I do not know who they are, and may be you can spare one minute to elucidate for the benefit of people like me who do not know all the technicalities involved. But I believe you agree with me that the people who issue an upgrade are ultimately responsible for its good operation, no matter if some of the parts making up the product, or necessary for the working of the product, are developed elsewhere. And this includes routers. By the same token, a manager is ultimately responsible for the mistakes of his subordinates.

---

### Post by howefield on 2009-12-13
> **coredeal said:**
> I mean, it's unacceptable.

It may be, but what is more acceptable is the quality and quantity of your alternative choices. Firefox isn't the only browser worthy of the name.

---

### Post by Jefferythewind on 2010-02-07
Hi everyone,

You've only had five cups of Ubuntu to this point, so the first thing we all should do is take a deep breathe.  I have had no problem at all with my Karmic Koala, or firefox, and I am pleased to be an Ubuntu-based computer user.  I have a Thinkpad x61s and it is so smooth.

  I just tried installing Ubuntu on my friend's new custom computer, it is a 64 bit system, so i installed Ubuntu 9.10 64 bit.  Everything went fine, but I am having trouble installing adobe flash.  Every time after a fresh install you have download and install adobe flash in firefox.  When i try to install the .deb package, I get an error about i386.  I don't know how to install the other packages offered, and i didn't see anything about a 64 bit version.  It looks like there is a new version as an APT file type.  Does anyone know anything about this?

Thanks,

---

