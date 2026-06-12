---
title: "64-bit Hardy on M1330"
date: 2008-04-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by drsaamah on 2008-04-23
Has anyone out there tried 64-bit Hardy on the Dell M1330?  I've been using the beta version of Hardy for about a week now and I love it.  I think its a huge improvement (with the exception of making FF3 beta default) over Gutsy.  But anyways I just wanted to know what kind of troubles with hardware or stability anybody has encountered.  I have more memory than the 32-bit OS can recognize, so I'm kind of itching to switch :)

---

### Post by jespdj on 2008-04-23
I have an M1530 and 64-bit Hardy RC [works great]("http://jesperdj.pbwiki.com/Ubuntu-on-the-Dell-XPS-M1530") on it. The M1330 is not very different from the M1530, so it will probably work well.

---

### Post by chrisdugdale on 2008-04-23
I got a Dell Dimension E521 (Athellon 64 x2) so this doesn't directly apply. Been using Gutsy for months and Hardy 8.04 beta for about 10 days. Most of the glitches I got with the AMD64 were to do with unavailable or incomplete applications or driver problems. Even Java and stuff like that has greatly improved recently and for the last few weeks I've had a fully working system, with the final touch coming in the last week or so. I would have recommended sticking to the 32bit Ubuntu for most people a few weeks ago, now I reckon that 64bit rocks real fine. It helps that the Nvida driver seems more stable too.

---

### Post by adw on 2008-04-23
Hi!
Got the m1330 and the 64-bit Hardy. 
I did an upgrade to 64 due to my 4gb of ram, and so far its worked out fine.
I dont know, but to me it feels better :-) but thats probably related to the ram. No issues apart from the usual ones like the thinkfinger, but thats the same as with the 32-bits version- so no big "dealbreakers" here:popcorn:

---

### Post by jespdj on 2008-04-23
adw, did you get thinkfinger working? That's the only thing I haven't got working on my M1530 at the moment.

---

### Post by adw on 2008-04-23
Yes, with help from synaptic and [https://wiki.ubuntu.com/ThinkFinger](https://wiki.ubuntu.com/ThinkFinger) thinkfinger is working good.
Notice that the repos are available in Hardy synaptic, so you don't have to manually add the software sources.

If you follow the wiki tut, just download thinkfinger-tools and libpam-thinkfinger from synaptic, then skip to the "Test the fingerprint reader" part on the wiki and follow through. You should be sorted ;)

Oh! remember to edit /etc/pam.d/common-auth like the wiki says.
After that i had to reboot, but apart from that all works perfect.

---

### Post by jespdj on 2008-04-23
Aha, I did install thinkfinger-tools but not libpam-thinkfinger. Thanks!

---

### Post by drsaamah on 2008-04-23
Wow, thanks for all the feedback everyone!!  This is much better feedback than I was expecting.  Looks like I'll be switching to 64-bit this weekend then :)

---

### Post by ethanay on 2008-04-24
let us know how it goes, drsaamah!

ethan

---

### Post by bioburg on 2008-04-24
Still using Gutsy 64 bit on my M13330.

I really like it so far. The only thing I can't get working is the integrated microphone. There only seems to be a fix for the 32 bit version ....

Also having some problems getting games running in a VM (2D based). But that's not 64 bit related ;-)

Have fun upgrading m8 :-)

---

### Post by drsaamah on 2008-04-25
Wow... okay so everything is GREAT with one little exception...
The repos for the 64-bit kinda suck.  And my kinda suck I mean my absolutely beloved favorite media player ever is missing... ie banshee.  So here's where my computer idiocy comes in...
Can 64-bit OS's run 32-bit programs?  If so, then I should be able to just banshee from source no problem, right?  If not... well then I suppose I'll just cry until I find a new substitute for banshee.
Other than that, is the set up for thinkfinger the same as it was for 32-bit Ubuntu?
Thanks advance for all the help guys!

---

### Post by drsaamah on 2008-04-26
NEVER MIND.  I'm an idiot.  Everything I need is in the repositories and 64-bit Hardy is working GREAT!  However, for bettering my understanding of computers... if I did want some program that wasn't in the repositories, and the program was only available in 32-bit... would I be able to compile and use it on a 64-bit system?  Or am I restricted to software written for a 64-bit platform from now on?  And thanks again for all the prior feedback!

---

### Post by bioburg on 2008-04-26
@drsaamah: Sounds you are trying to do, what I want to do if I'm confident that all my hardware is supported. So tnx for taking the test approach for me ^^.

I'm using Gutsy 7.10 64 bit on my M1330. 

I did stumble on some software related 32bit available, 64bit non-available problems.
In my case it were using BlueJ (for school) and using Wine (just don't seem to startup right) --> using XP 32 bit via virtual box helped me out of these problems.

I also stumbled against some hardware problems. I got (almost) everything working except these:

-Hybernation / sleep when closing the lid --> It won't wake up when I try to resume and all video / audio settings are screwed up after the necessary 10 sec start button push ^^
-Some extra power savings methods --> low energy consumption when disconnected for AC. (full battery on Ubuntu = around 2,5 hours vs full battery on Vista energysavings mode = 4 hours)
-The integrated microphone --> I did manage to get an external mic to work but not while using chat programs like aMSN. And ofcourse I prefer to use the integrated one.

I'm thinking of upgrading to 8.04 but I just hope not all of my settings/VMs/programs have to be set again :/

I should probably backup all:
/home/user
*including*
/home/user/.VirtualBox/Machines/ 
to an external drive before doing the upgrade since I hear it can give some problems and it's better to do a clean install :/

If I place them back all files and VMs should work like the were doing right?

Have fun with the your new gadget m8 :D

---

### Post by drsaamah on 2008-04-26
I would imagine that since you already have 64-bit Gutsy, doing an upgrade (as opposed to a clean install) should leave your virtual machine set-up unmodified.  I might be wrong though, I haven't played with vmware or anything else of this sort since I switched to Linux.  I can tell you however, that overall Hardy has made a lot of little improvements over Gutsy.  I had very few problems with Gutsy and even less now with Hardy!  This is a hell of a step foward for Ubuntu!!

---

### Post by ethanay on 2008-04-28
you can always locate the specific config files that you need, and back them up and copy them back to the directory after a fresh install.

I backed up my entire home folder, but only replaced the hidden folders or parts thereof that contained files or settings that I wanted to retain (e.g., mozilla bookmarks, etc)

also, download and try aptoncd if you don't want to go hunting for programs after install :)

---

### Post by Gooler on 2008-04-30
I got it installed a week ago. The only problem I see is the lack of i8kutils package and module.

It's a fresh installed kubuntu.

---

### Post by bioburg on 2008-04-30
> **drsaamah said:**
> I would imagine that since you already have 64-bit Gutsy, doing an upgrade (as opposed to a clean install) should leave your virtual machine set-up unmodified.  I might be wrong though, I haven't played with vmware or anything else of this sort since I switched to Linux.  I can tell you however, that overall Hardy has made a lot of little improvements over Gutsy.  I had very few problems with Gutsy and even less now with Hardy!  This is a hell of a step foward for Ubuntu!!

Sounds good ^^

Does your hybernate option work? 
And your integrated microphone?

Those are the only 2 things I haven't got working atm :-)

I will keep the advice of ethanay in mind and probably do the upgrade soon. 

Keep you posted :D

---

### Post by PhrygianCat on 2008-05-06
So, my M1330 is arriving tomorrow. I ordered it only with 2GB memory. My question, do you think it's better to stick with 32-bit or should I go with 64-bit? And what's the memory restriction for 32-bit? I'm not able to find information on that.

---

### Post by akniss on 2008-05-06
I just upgraded my m1330 to 4 gigs of memory (2x2G).  I put 32-bit Hardy on it and it recognizes 3.5 GB.

---

### Post by hoodieboy711 on 2008-05-25
I just bought my m1330 and it seems to be working exceptionally minus a couple of things:

- Internal Microphone
- Media control buttons: I don't know if I have to do something special to map them to applications, etc.
- Volume: Its full volume at 100% but 3 or 4 clicks down (about 75%), the volume is quiet enough that it's virtually muted.

I've been searching forums and I can't find anything on how to get either of these working.  And a lot of the time it seems that these are working out of the box for some people, like the media buttons.

Anyone got any ideas?

---

### Post by LK_gandalf_ on 2008-05-26
Kubuntu 8.04 64bit works great on my Dell XPS 1530, which is very likely the 1330.

---

### Post by Reynolds on 2008-07-10
I'm new to ubuntu and I have ordered a xps m1330 (which should be arriving soon) and I wondered whether to install the 64 or 32 bit version. The major requirement for me is being able to run Matlab (a linux 32-bit version i already have running at work), Python and mostly MayaVi2 (TVTK tookit) to display results as 3D graphs, and to run vmware appliances to test applications under development in various platforms. 

Thanks in advance for your help!

---

### Post by Salomonis on 2008-07-15
I only have a gig of memory, but it's been bothering me that I have a 64 bit motherboard if I press the switch.  The first question on my mind is what application makes 64-bit worth it for Hardy Heron?  I've been hearing everywhere that you need at least 4GB of Ram before considering it.  My other question is what program doesn't run well with 4GB of Ram on Hardy Heron at 32-bit?

---

### Post by drsaamah on 2008-07-15
You don't *need* 4 gigs of ram before considering switching to 64-bit operating system.  What you *need* is simply a 64-bit processor (well, and 64-bit chipset).  As far as applications that make it worth switching, the list isn't long.  Really, if you program and are constantly compiling codes on your computer then you're going to want to switch to a 64-bit operating system.  There are definitely no programs that don't run on 64-bit.  They just act as a 32-bit program.

---

### Post by Salomonis on 2008-07-20
I have the chipset.  Athlon 64 3000+.  It was one of those motherboards that had the option.  939Dual-Sata2 ASRock  I just don't like slowly upgrading I don't have SATA harddrives.  Wish I had the money to kill, don't we all.

---

### Post by distobj on 2008-08-01
I'm wondering what approach you all have taken to upgrading from 32 to 64 bit?  I don't suppose it's as easy as using synaptic, or making a change to /etc/apt/sources.list eh?

---

### Post by drsaamah on 2008-08-01
No unfortunately, you're going to have to do a clean install in order to go from 32-bit to 64-bit.

---

