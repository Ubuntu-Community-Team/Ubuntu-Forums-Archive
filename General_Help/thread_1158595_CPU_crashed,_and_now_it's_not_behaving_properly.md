---
title: "CPU crashed, and now it's not behaving properly"
date: 2009-05-13
forum: General Help
---

### Post by bneva on 2009-05-13
I wasn't sure where to put this so I figured this would be the best place.  I am still kind of new to linux so bare with me....  I am currently dual booting ubuntu/xp

The story goes like this, I was in class I opened a youtube video up and the sound was playing but something happened.  I could move the mouse around and not click anything (the sound still going).  So I turned my laptop off VIA the power button and back on and now:
 
-I have random blue blocks all over on the first loading screen
-When grub loads I have ASCII characters randomly all over the screen.
-Ubuntu wouldn't even start until I tried the recovery mode stuff, fix packages etc... during this there was ASCII characters all over the screen
-Now ubuntu starts but only in 800x600 and there's yellow stripes across my screen.
-I can't even get into windows unless it's in safe mode

Has this happened to anyone else?  am I totally screwed?

Thanks in advance!

---

### Post by stathol on 2009-05-13
I hate to say this since we're talking about a laptop, but it sounds like your video card bought the farm. That's probably what caused your initial hang, too. If you're lucky, your laptop isn't using an integrated GPU. That would make it considerably easier to replace. If it has integrated graphics on the MB, then there's not a lot to be done other than to send it back to the factory for a refurb, since there's almost no way to get your hands on the particular MB used in your laptop even if you were inclined to replace it yourself.

---

### Post by bneva on 2009-05-13
sigh, I really don't want to get another graphics card....  Yea it's not an onboard one it's a GeForceGo 9750GTX I Believe.  But I mean why would windows not even load and ubuntu would?

heres a few pics


[http://i3.photobucket.com/albums/y89/st1fler/DSC02002.jpg](http://i3.photobucket.com/albums/y89/st1fler/DSC02002.jpg)
[http://i3.photobucket.com/albums/y89/st1fler/DSC02004.jpg](http://i3.photobucket.com/albums/y89/st1fler/DSC02004.jpg)
[http://i3.photobucket.com/albums/y89/st1fler/DSC02006.jpg](http://i3.photobucket.com/albums/y89/st1fler/DSC02006.jpg)
[http://i3.photobucket.com/albums/y89/st1fler/DSC02008.jpg](http://i3.photobucket.com/albums/y89/st1fler/DSC02008.jpg)

---

### Post by collinp on 2009-05-13
I have to agree with the person above, sounds like your video card bit the dust. It is definitely a hardware problem, and something major.

I cant explain how Ubuntu boots and Windows does not, Windows relies upon one driver to boot while Ubuntu has the proprietary Nvidia driver and the open-source nvidia driver to use.

---

### Post by bneva on 2009-05-13
that's unfortunate to hear :(  Well thanks, I guess I'll look into a new one

---

### Post by petrus4 on 2009-05-13
> **bneva said:**
> that's unfortunate to hear :(  Well thanks, I guess I'll look into a new one

You might want a new distribution while you're about it.  I've had sound issues and a video card crash myself.

Ubuntu installs power management software which can potentially control the fan and do seriously bad things to hardware.

Linux is an operating system that requires people to take some personal responsibility.  Using the "user friendly," option, where you don't have to invest any time or effort whatsoever, is only likely to cause you problems, long term.  If you really want to use Linux, go and download [Slackware]("http://www.slackware.com/") and learn.

There is no free lunch.

---

### Post by Skripka on 2009-05-13
> **petrus4 said:**
> You might want a new distribution while you're about it.  I've had sound issues and a video card crash myself.

Ubuntu installs power management software which can potentially control the fan and do seriously bad things to hardware.

Linux is an operating system that requires people to take some personal responsibility.  Using the "user friendly," option, where you don't have to invest any time or effort whatsoever, is only likely to cause you problems, long term.  If you really want to use Linux, go and download [Slackware]("http://www.slackware.com/") and learn.

There is no free lunch.

I would refrain from recommending Slackware to a user new and fresh to Linux.

As far as explaining the behavior...I'd wager that Ubuntu is reverting to generic enough VESA drivers to give you something of a GUI-as it detected your GPU bought the farm abd was unresponsive.

---

### Post by chili555 on 2009-05-13
> i would refrain from recommending slackware to a user new and fresh to linux.+1000

---

### Post by bneva on 2009-05-13
thanks for the replies guys!  I appreciate it, I will look into getting a new card.

---

### Post by Skripka on 2009-05-13
> **bneva said:**
> thanks for the replies guys!  I appreciate it, I will look into getting a new card.

Since you're on a new laptop-look into warranty claim.  Paying out of pocket to repair a notebook usually costs more (depending on the problem) than buying an entirely new machine.

---

### Post by petrus4 on 2009-05-13
> **Skripka said:**
> I would refrain from recommending Slackware to a user new and fresh to Linux.

That depends on said user's level of intelligence and/or initiative.  It was the first distribution I used.

Even if Slack isn't the first distro someone uses however, it's still in their best interests to become sufficiently competent that they're willing to use it or something similar ASAP.

Ubuntu is a mess.

---

### Post by Skripka on 2009-05-13
> **petrus4 said:**
> That depends on said user's level of intelligence and/or initiative.  It was the first distribution I used.

Even if Slack isn't the first distro someone uses however, it's still in their best interests to become sufficiently competent that they're willing to use it or something similar ASAP.

Ubuntu is a mess.

Perhaps, for you.  Going from a GUI rich easy distro to system with no depend tracking is a recipe for frustration, in most cases.

---

### Post by petrus4 on 2009-05-13
> **Skripka said:**
> Perhaps, for you.  Going from a GUI rich easy distro to system with no depend tracking is a recipe for frustration, in most cases.

Have you actually tried doing it?

Most of the problems people are writing about in this forum, I've never seen people having with any other Linux distro.  I have, however, seen people reporting similar things with Windows tech support before.

That's the direction Ubuntu is headed in.  The initial learning curve might be steeper with something else, yes; but if you think that long term, Ubuntu means less frustration than an actual **Linux** distribution, you obviously haven't tried it yourself.

Ubuntu is **not** easy.  Look around; someone just started a thread about how Jaunty has randomly, degeneratively become completely hosed.  His petitions aren't being found, and his machine just goes to a black screen.  Nothing is working for him.

Is that easy or "user friendly?"

Other Linux distributions are discoverable.  Other Linux distributions are reliable.  In the incredibly rare instance that something breaks, you can go in and fix it, and if you have experience, you will generally know exactly where **to** go as well.  Things don't just die all of a sudden, randomly and mysteriously.

That isn't Linux's normal behaviour; it's a lot closer to Windows'.

Seriously; when Ubuntu has been reduced to the sort of bloated, randomly crashing, crawling mess that Vista is, or Windows ME was, some of you are probably going to wonder why you bothered migrating away from Windows in the first place.

In trying to clone Windows, Ubuntu is also cloning Windows' problems.

Say whatever else you want, but don't accuse me of ignorance when other people in here are reporting these kinds of problems.  In technical terms, Ubuntu **is** certifiable garbage, at a systemic level, and that is demonstrable by virtue of the fact that if it wasn't, the people here wouldn't be having the sorts of problems that they are.

---

### Post by Skripka on 2009-05-13
> **petrus4 said:**
> Have you actually tried doing it?

Most of the problems people are writing about in this forum, I've never seen people having with any other Linux distro.  I have, however, seen people reporting similar things with Windows tech support before.

That's the direction Ubuntu is headed in.  The initial learning curve might be steeper with something else, yes; but if you think that long term, Ubuntu means less frustration than an actual **Linux** distribution, you obviously haven't tried it yourself.

Seriously; when Ubuntu has been reduced to the sort of bloated, randomly crashing, crawling mess that Vista is, or Windows ME was, some of you are probably going to wonder why you bothered migrating away from Windows in the first place.

In trying to clone Windows, Ubuntu is also cloning Windows' problems.

Telling someone with dead or faulty hardware, who is new to Linux, to go to Slack is not wise.  You'll note I use Arch and not Ubuntu by my sig.  Most users new to Linux want hand-holding GUIs even if it means sacrificing performance, yes.... and are also scared of the CLi.  Shall we agree to disagree, and let the OP have his own topic?

---

### Post by petrus4 on 2009-05-13
> **Skripka said:**
> Most users new to Linux want hand-holding GUIs even if it means sacrificing performance, yes.... and are also scared of the CLi.  Shall we agree to disagree, and let the OP have his own topic?

We're not disagreeing on that.

I'm not suggesting necessarily that new users should not a hand holding GUI, at least for a certain period; purely that I really don't think that this particular one has been designed well at all.

---

### Post by Crafty Kisses on 2009-05-14
> **Skripka said:**
> I would refrain from recommending Slackware to a user new and fresh to Linux.

As far as explaining the behavior...I'd wager that Ubuntu is reverting to generic enough VESA drivers to give you something of a GUI-as it detected your GPU bought the farm abd was unresponsive.

Not to start a flame or anything, but I wouldn't refrain him from using any Linux distribution, heck use Slackware. It's a great learning experience. You might even want to try looking at Gentoo. Both great distributions of Linux and it gives you a feel of how everything works. 

That said, there's so much documentation on both of those distributions of Linux it's crazy, so if he has any problems he can revert to the forums, documentation and the IRC rooms they have open for those distributions. The Gentoo documentation and forums are ridiculously helpful, along with the IRC room. 

Now I will say Slackware / Gentoo are not for the faint of heart. I guess you could consider those power distributions, but I say within a couple of weeks you can at least have your system up and running decently and have expanded your Linux knowledge and in the long run, it feels good to learn more about Linux.

---

### Post by bneva on 2009-05-14
haha look what I started!  Yea my laptop is currently not under warranty anymore, I only got the year warranty and I've had it for 1.5 years now.

and I don't plan on switching to a different version of linux, atleast not yet haha.  I only got it originally for one of my classes at school where I have to do linux programming.

---

### Post by chili555 on 2009-05-14
> Look around; someone just started a thread about how Jaunty has randomly, degeneratively become completely hosed. His petitions aren't being found, and his machine just goes to a black screen. Nothing is working for him.And if his problem, as suspected by most of us here, is either a deceased graphics card or CPU, Slackware can fix that...how?> Things don't just die all of a sudden, randomly and mysteriously.Hardware often does just that and Slackware, Windows, OSX nor Ubuntu has not much it can do to help or hurt old age, poor manufacturing techniques or poor design. This whole issue is masked in the Windows world, because when the computer gets bogged down with virii and spy-ware and when the next patched on patched version of Windows comes out, many just buy a new computer. Only with Linux are you able to install and run a very capable operating system on a 10-year-old laptop. Hardware fails at a greater rate after ten years of use than in three years of use.

My wife and I have been running Linux, including Ubuntu, Fedora and Arch, full time since 2001. Any suggestion that Ubuntu is bloated and crash-prone is very far from our experience.

---

