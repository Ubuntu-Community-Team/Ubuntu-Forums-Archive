---
title: "Which Video Card to get?"
date: 2010-08-10
forum: Gaming &amp; Leisure
---

### Post by gloken on 2010-08-10
Last night I spent six hours trying to get StarCraft 2 work with my ATI card. It wouldn't even boot on the Open Source drivers, and the Proprietary drivers leave me with garbled text and graphics.  After reading every troubleshooting tip, tutorial, and upgrading everything and its dog as far it'd go, I'm about done with Catalyst.

In short, I'm thinking nvidia is the way to go. Time to spend money. Anyone have any advice on what card runs StarCraft II best under Ubuntu?

I'm looking at: Nvidia Geforce 9800GTX+ as SC2 recommends the 9000 series, and this one is on the Ubuntu supported hardware list.

---

### Post by ed-koala on 2010-08-10
I run dual 9800GTX+ cards and Wine runs WoW beautifully.  I loaded Starcraft and it works also.  Not sure about Starcraft 2 but I hear it works almost 100%.  Check out the Wine HQ database for more info.  Nvidia is the way to go, ATI is getting better but it isn't quite as good as nvidia under Ubuntu yet imo.

---

### Post by sprocket10 on 2010-08-10
I'm not sure if nVidia's new GTX 460 is supported by Ubuntu yet, but if it is, that's what I'd go for! I hear it handles SC2 wonderfully

---

### Post by ed-koala on 2010-08-10
You can also be sure if SC2 under Wine has bugs, they will be addressed.  Wine keeps up with changes to WoW pretty quickly.  I'd expect things to be the same with SC2.

---

### Post by gloken on 2010-08-10
To narrow this discussion down a bitm I called the local computer store (I'm in a small town, so options are limited) and they've got an 8500GT and the EN GT240 sitting on their shelf.

Wouldn't be my first pick... but a Google search hasn't turned up too much bad news so far.

---

### Post by Perfect Storm on 2010-08-10
What's your budget for a new card? If you want a gaming card go for nvidia card that have the three letters in them: gtx you can't go wrong with such cards.

---

### Post by gloken on 2010-08-10
> **Artificial Intelligence said:**
> What's your budget for a new card? If you want a gaming card go for nvidia card that have the three letters in them: gtx you can't go wrong with such cards.

I'm throwing money at my problems to make them go away. ;) As long as I'm blinded by annoyance, cost isn't a factor. heh.

---

### Post by Perfect Storm on 2010-08-10
Okay. If your motherboard support PCIexpress x16 get a card like nvidia gtx285 1GB DDR3 Ram (and it uses 20% less power than my old 8800gtx) or better.
I got such card and it runs everything smoothly even highend stuff via wine.

---

### Post by Simian Man on 2010-08-10
> **gloken said:**
> I'm throwing money at my problems to make them go away. ;) As long as I'm blinded by annoyance, cost isn't a factor. heh.

Running games with wine is always an exercise in annoyance.  If you don't mind spending money, why not just pick up a copy of Windows where your ATI card and SC2 will run great.

---

### Post by cascade9 on 2010-08-10
> **gloken said:**
> Last night I spent six hours trying to get StarCraft 2 work with my ATI card. It wouldn't even boot on the Open Source drivers, and the Proprietary drivers leave me with garbled text and graphics. After reading every troubleshooting tip, tutorial, and upgrading everything and its dog as far it'd go, I'm about done with Catalyst.

In short, I'm thinking nvidia is the way to go. Time to spend money. Anyone have any advice on what card runs StarCraft II best under Ubuntu?

I'm looking at: Nvidia Geforce 9800GTX+ as SC2 recommends the 9000 series, and this one is on the Ubuntu supported hardware list.

I wouldnt be quite so quick to blame ATI, WINE isnt an exact science, and there are lots of people with SC2 probems with windows. 

I dont know where you found someone recommending 9XXX series, this is what they actually list as the requirements- 

>             **PC Minimum System Requirements*:**         
   
[LIST]
[*]Windows® XP/Windows Vista®/Windows® 7 (Updated with the latest Service Packs) with DirectX® 9.0c
[*]2.6 GHz Pentium® IV or equivalent AMD Athlon® processor
[*]128 MB PCIe NVIDIA® GeForce® 6600 GT or ATI Radeon® 9800 PRO video card or better
[*]12 GB available HD space
[*]1 GB RAM (1.5 GB required for Windows Vista®/Windows® 7 users)
[*]DVD-ROM drive
[*]Broadband Internet connection
[*]1024X720 minimum display resolution
[/LIST]
              **PC Recommended Specifications:**         
   
[LIST]
[*]Windows Vista®/Windows® 7
[*]Dual Core 2.4Ghz Processor
[*]2 GB RAM
[*]512 MB NVIDIA® GeForce® 8800 GTX or ATI Radeon® HD 3870 or better
[/LIST]
 [http://us.blizzard.com/support/article.xml?articleId=26242&locale=en_US](http://us.blizzard.com/support/article.xml?articleId=26242&locale=en_US)

> **gloken said:**
> To narrow this discussion down a bitm I called the local computer store (I'm in a small town, so options are limited) and they've got an 8500GT and the EN GT240 sitting on their shelf.

Wouldn't be my first pick... but a Google search hasn't turned up too much bad news so far.

Both cards, IMO, will be at least 'meh' with SC2 under WINE. Just not enough power. See this- 

> I mentioned earlier this month that I was enjoying the Starcraft 2 beta on Ubuntu 10.04 thanks to Wine software. In my previous posting I had simply stated that SC2 was "playable" under Wine. I have a fairly powerful gaming laptop that sports an nVidia 260m GTX and a 1680x1050 resolution panel. SC2 defaulted itself under Wine to "ultra" settings on my system - after playing one game at these settings (well it was really more like playing a slide-show). I promptly lowered the details and textures to low (while leaving the resolution the same).

With these settings I average around 40 FPS at the main menu and in game. At the high end I see just over 50 FPS while playing and at the low end it bottoms out around 20 FPS in combat.

Snip!  

Needless to say it performs better, in fact the FPS I see under low settings on Wine is about equal to the same FPS I was seeing under high settings on Windows. That is about where the things that worked better under Windows ended for SC2 on my computer.[http://www.wine-reviews.net/wine-reviews/news/starcraft-2-and-a-bit-of-wine-and-linux-performance.html](http://www.wine-reviews.net/wine-reviews/news/starcraft-2-and-a-bit-of-wine-and-linux-performance.html)

That was with a GTX260M, which has a lot more sharders, texture mapping uints and render outputs (112, 56, 16, 256bit memory interface and 550MHz core for GTX260M) than a GT240 (96, 32, 8, 128bit and 550MHz core) or worse yet a 8500GT (16, 8, 8, 128bit, 450MHz core). 

I'd be looking for at least a GTS250 (128, 64, 16, 256bit, 738MHz core...which is the same as the GTX9800+, but the GTS250 has some minor improvments over the older GTX9800+) or better. A GTX260 or higher would be your best bet.

---

### Post by gloken on 2010-08-10
> **Simian Man said:**
> Running games with wine is always an exercise in annoyance.  If you don't mind spending money, why not just pick up a copy of Windows where your ATI card and SC2 will run great.

I'd rather not get into this debate, but I'll assume this was asked in good faith and not general trollery. See I'm no ideologue, and I do have an XP key, so that'd be a "free" solution.

However:

1) I would much rather not have an entire OS dedicated to an individual piece of software.
2) I'd rather not try to build a dual boot with Windows as the second OS (as the first it's easy!) and a quick search on the process of rebuilding boot loaders should demonstrate why.

I'd much rather toss in new hardware and move on with my life. Hope that clears it up. ;)

---

### Post by Rumpletumbler on 2010-08-10
> **cascade9 said:**
> I wouldnt be quite so quick to blame ATI, WINE isnt an exact science, and there are lots of people with SC2 probems with windows.

It seems their older cards aren't well supported. I have a Radeon 9700 Pro and in Urban Terror in Windows get 90+ FPS and in Ubuntu low 20's which makes it unplayable on the Ubuntu side. I've left Windows for good so I won't be playing until I can buy another card. Just an observation, not trying to throw cold water on your statement.

---

### Post by LowSky on 2010-08-10
> **sprocket10 said:**
> I'm not sure if nVidia's new GTX 460 is supported by Ubuntu yet, but if it is, that's what I'd go for! I hear it handles SC2 wonderfully

it does work... but using the newer 256 dirver is really recommended

Source= ME

---

### Post by gloken on 2010-08-10
> **cascade9 said:**
> I wouldnt be quite so quick to blame ATI, WINE isnt an exact science, and there are lots of people with SC2 probems with windows. 

I dont know where you found someone recommending 9XXX series, this is what they actually list as the requirements- 

[http://us.blizzard.com/support/article.xml?articleId=26242&locale=en_US](http://us.blizzard.com/support/article.xml?articleId=26242&locale=en_US)



Both cards, IMO, will be at least 'meh' with SC2 under WINE. Just not enough power. See this- 

[http://www.wine-reviews.net/wine-reviews/news/starcraft-2-and-a-bit-of-wine-and-linux-performance.html](http://www.wine-reviews.net/wine-reviews/news/starcraft-2-and-a-bit-of-wine-and-linux-performance.html)

That was with a GTX260M, which has a lot more sharders, texture mapping uints and render outputs (112, 56, 16, 256bit memory interface and 550MHz core for GTX260M) than a GT240 (96, 32, 8, 128bit and 550MHz core) or worse yet a 8500GT (16, 8, 8, 128bit, 450MHz core). 

I'd be looking for at least a GTS250 (128, 64, 16, 256bit, 738MHz core...which is the same as the GTX9800+, but the GTS250 has some minor improvments over the older GTX9800+) or better. A GTX260 or higher would be your best bet.

Interesting. Thanks. I'm blaming ATI because I'm 90% sure this is a Catalyst driver problem, based on my troubleshooting and all of the reading I've done online. I've always had some issues with the card, so losing it doesn't seem like a major loss anyway - and aside from some major 3d graphics glitches, it's all running pretty well.

---

### Post by rizzeh on 2010-08-10
try looking at the problem another way: What is the heaviest linux native game? Has to be Quakewars and 9800GTX would cut it with QW. So really pick any card equal or better as long as its nVidia. 
I've used linux since 2005 and nvidia drivers are by far the best and pain free.

---

### Post by Arthur_D on 2010-08-10
I have the NVIDIA GeForce GTS 250, and IMO it's a really good card, so I'd have to chime in and say get it or if you care to spend the money, an even better one from NVIDIA.

I've always used NVIDIA, and I can't recall when I last time had any trouble with it.

---

