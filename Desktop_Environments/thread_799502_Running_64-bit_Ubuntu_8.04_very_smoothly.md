---
title: "Running 64-bit Ubuntu 8.04 very smoothly"
date: 2008-05-19
forum: Desktop Environments
---

### Post by anjanesh on 2008-05-19
Im not looking for [recommended minimum requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements") for a desktop to use Ubuntu 8.

The last time I used Linux, it was FC2 on a PIII with 128MB RAM and it look *minutes* to load OpenOffice.

Im looking for a much-more-than-enough to use Linux (dual-boot Ubuntu 8.04 64-bit & FC9 64-bit).

Will a PC like [this]("http://h10010.www1.hp.com/wwpc/in/en/ho/WF06b/1090261-1111625-1123043-1123043-1123043-81733580-81813134.html") with 2GB RAM (unfortunately max capacity is 2GB) be more-than-sufficient to run Ubuntu 8.04 64-bit real smoothly ?
Or do I need to opt for something like [this]("http://h10010.www1.hp.com/wwpc/in/en/sm/WF06b/1090261-1139371-1139371-1139371-81721208-81721211-81743199.html"), [this]("http://h10010.www1.hp.com/wwpc/in/en/sm/WF06b/1090261-1139371-1139371-1139371-81721208-81721213-81743201.html"), [this]("http://h10010.www1.hp.com/wwpc/in/en/sm/WF06b/1090261-1139371-1139371-1139371-81551567-81551568-81733551.html"), [this]("http://h10010.www1.hp.com/wwpc/in/en/sm/WF06b/1090261-1139371-1139371-1139371-81551567-81551569-81733559.html"), [this]("http://h10010.www1.hp.com/wwpc/in/en/sm/WF06b/1090261-1139371-1139371-1139371-80583673-80583677-80781720.html"), [this]("http://h10010.www1.hp.com/wwpc/in/en/sm/WF06b/1090261-1139371-1139371-1139371-80583673-80583674-80781726.html"), [this]("http://h10010.www1.hp.com/wwpc/in/en/sm/WF06b/1090261-1139371-1139371-1139371-82225966-82231223-82231227.html") which have a max-capacity of 8GB RAM and going to cost more than double ? 

Thanks

---

### Post by p_quarles on 2008-05-19
The first option there will run it just fine, and is definitely "more-than-sufficient." It runs smoothly for me on a computer about half as powerful as that one.

---

### Post by cgrenier on 2008-05-19
I've run 64-bit Ubuntu (Edgy, I think) perfectly well, flawlessly  with compiz and everything, on a dual-core 3800+ with 1G Ram and an Nvidia 6800.  And that was overkill.  Now I am running Hardy 32 bit on the same system but with 1G more ram, and it's still perfectly smooth and fast.  Openoffice opens in seconds -- they have improved a lot in that regard.

So yes, you can run Ubuntu with full effects - Compiz, Gnome, desktop widgets galore, all the visual effects you could want - without any slowdown on that machine.  Although I'm not sure how good that integrated GPU is... 

In any case, you could always run Xubuntu or a Fluxbox type system which will be fast no matter what computer you're running on.

---

### Post by anjanesh on 2008-05-19
I want to run Ubuntu Hardy 64-bit on a machine which can support 4GB/8GB RAM with 4MB cache so that I can upgrade RAM when required.

But whats [this]("http://ubuntuforums.org/showthread.php?t=375853") about Ubuntu 64-bit not being able to recognize 4GB as easily as it should be. Do I need to tweak stuff if I do for like 8GB of RAM ?

---

### Post by drifter0000 on 2008-05-19
around december I installed Mint 4.0 dual boot with win xp Pro on P3 with 768mb 100mhz memory and Nvidia 6200 with 256mb mem AGP.  It ran fine even though agp card ran at lowest level because old motherboard didnt support AGP x8.

Now I built new computer with Amd 64 3800 running at 2.40mhz and 1gb 400mhz memory.

I put the Nvidia 6200 in the new motherboard because it supported AGP x8 and I cant afford a new video card.

Results are I run 8.04 64bit with full compiz effects and emerald. While im writting this from firefox my system says 2.0% cpu load and 385 Mb memory used.  It runs like lightning for me.

---

### Post by anjanesh on 2008-05-19
I've noticed that the majority who use the 64-bit version are using it on an AMD instead of Intel.

Would more RAM mean eliminating hard-disk swap memory ?

---

### Post by Sef on 2008-05-19
I use 8.04 64-bit with 2 gb ram.  I have no problems with my set up or things running slow.  I did set up 1 gb swap, but it is not really used and I could do without it just fine.  I don't do anything really cpu intensive that much.

---

### Post by anjanesh on 2008-05-19
Thanks for your replies - I've decided to go for a config that can support 8GB RAM, though I'll be getting only 2 or 4 gigs for now. The first link's config has a max capacity of 2GB so even if I wanted to have more later on, it wouldnt be possible.

I still feel 2GB is still not-all-that-sufficient when you have high GUI apps running on Java platform. OpenOffice3 supports Office 2007 formats etc - using Abiword instead of OO is not an alternate solution.
Applications like NetBeans & Eclipse are memory hogs.

---

### Post by dppowell on 2008-05-29
FWIW (probably very little), I just installed 64-bit Hardy on my new HP dv9700t (Intel T9300, 3 GB RAM) notebook today and it's flying with all sorts of eye candy running.

---

### Post by Hooya on 2008-05-30
I have an Athlon 64 3200+ with 1GB of RAM and Hardy 8.04 64-bit is smooth as silk.

OpenOffice Word processor starts in 7 seconds cold.  Less than 2 seconds if I recently closed it.  I almost never use more than 10MB of swap space, and only then when I'm doing (or recently did) some gaming or unzipping a huge (4gb) archive.  I'm running CompizFusion with loads of visual effects including transparency and cube.

Even with the effects the OS is way smoother than Vista SP1 64 bit with many visual effects off and tweaks applied on the same machine.

---

