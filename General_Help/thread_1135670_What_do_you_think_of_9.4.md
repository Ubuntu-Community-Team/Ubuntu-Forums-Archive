---
title: "What do you think of 9.4"
date: 2009-04-24
forum: General Help
---

### Post by Anxious Nut on 2009-04-24
I want to know if ubuntu 9.4 is good or not! Does it has problems? Is it better than ubuntu 8.10? Should i switch/upgrade to it?

Thanks,
Anxious Nut

---

### Post by Mistoffeles on 2009-04-24
> **Anxious Nut said:**
> I want to know if ubuntu 9.4 is good or not! Does it has problems? Is it better than ubuntu 8.10? Should i switch/upgrade to it?

Thanks,
Anxious Nut

I don't know much about 9.4, but I love 9.04 so far. For one, it is the first Linux install where I have ever had RAID10 available as one of the software RAID options by default, without a lot of mucking about with the installation process or the installation ISO.

---

### Post by loveandequality on 2009-04-24
Yes you should but for some reason my compiz is not working at all must be my intel intregated card or i just need to restart now.

---

### Post by AlanR8 on 2009-04-24
Been using 9.04 since about Alpha 6 now and all is well. That said it's KUBUNTU so working with the KDE environment that just keeps getting better!

---

### Post by mb_webguy on 2009-04-24
I like it.  It's not a huge improvement over Intrepid, but the improvements are there, and noticeable.  Boot time is much faster, and the standard applets (Network Manager, Volume Manager, and Power Manager in particular) have some nice visual and functional improvements.

My only complaints so far are that the version of Amarok in the repos is Amarok 2 (and I think Amarok 1.4 is far superior), and the version of VLC has a few bugs (video can't be embedded in the player, and controls don't show up in fullscreen).  Of course, if you're happy using Rhythmbox and Totem, these don't matter.  And both can be resolved with the addition of a couple of PPAs.

---

### Post by Anxious Nut on 2009-04-30
Thanks for the replies:)

but I've heard that 9.4 has some issues with Intel graphics or some thing like that! is that true?

---

### Post by lisati on 2009-04-30
I can find 9.04 easily enough, but where do I get copies of 9.4? :confused:

---

### Post by blackgr on 2009-04-30
I find jaunty much lighter and improved. The total memory usage of my system is now 200-400 mb lower than the intrepid. As for intel cards, its true. There are perfomance issues with the driver, but there are some workarounds, like using older drivers from intrepid.

lisati: there is no 9.4. Everyone means 9.04

---

### Post by cybrsaylr on 2009-04-30
I like 9.04, it runs leaner and better than 8.10 did on an old Pent 2 PC I have 9.04 on.

---

### Post by muhannadfa on 2009-04-30
> **Anxious Nut said:**
> I want to know if ubuntu 9.4 is good or not! Does it has problems? Is it better than ubuntu 8.10? Should i switch/upgrade to it?

Thanks,
Anxious Nut

srry guys,
jaunty is buggy release
full of performance problem issues
if u cann't watch video's on OS what the heck
workaround they're talking about s not officail, and u can see, one saying working for me 10 saying nah! doesn't work
if u gonna try all the workarounds till u find the one it'll ineffective, which is not good
keep with 8.10, jaunty doesn't worth it till now, 
my advice wait for 9.10 > hope it's good
------------------------
issues with intel
issues with Nvidia
issues with ATI
issues with networking and routers
issues with Cpy over usage
>>>>>>> much much more<<<<<<<<<
------------------------------
that's my opinion

---

### Post by ubockto on 2009-04-30
'Tis good, I haven't any problems with sharing a printer with vista since I have upgraded from 8.10 to 9.04

---

### Post by El Zoido on 2009-04-30
9.04 is working quite nice for me, no major issues here.
I only encountered some minor oddities that could be resolved easly.
Boot-time has improved quite a lot for me.

Some of the issues I still have are with fullscreen video in totem (is working, but OSD is behaving strange) and VLC (bug, no OSD) and Flash performance ( I switched to 64bit, which still seems to have some issues with flash; nothing major though for me)

---

### Post by owoito on 2009-04-30
I have just upgraded my laptop from 8.10, to 9.04, and everything seems to be working perfectly. I am right now upgrading my desktop. Generally 9.04 feels very fast and light weighted and much more stable than 8.10. I am still playing around with it, but the over all impression is excellent. Thanks ubuntu team for a job well done.

---

### Post by skymera on 2009-04-30
> **muhannadfa said:**
> srry guys,
jaunty is buggy release
full of performance problem issues
if u cann't watch video's on OS what the heck
workaround they're talking about s not officail, and u can see, one saying working for me 10 saying nah! doesn't work
if u gonna try all the workarounds till u find the one it'll ineffective, which is not good
keep with 8.10, jaunty doesn't worth it till now, 
my advice wait for 9.10 > hope it's good
------------------------
issues with intel
issues with Nvidia
issues with ATI
issues with networking and routers
issues with Cpy over usage
>>>>>>> much much more<<<<<<<<<
------------------------------
that's my opinion

1) Jaunty hasn't had one problem with me since Alpha 5.
2) Performance problems? I boot in 11 seconds and memory usage is half what 8.10 used to be. 
3) I can watch videos even with Compiz on.
4) Haven't seen the workaround.
5) 8.10 was a terrible release.
6) My ATi worked perfectly with the FGLRX driver. People are having so many problems because ATi have stopped supported pre R500 chips.
7) Envy worked on my Nvidia card no problems.

Intel has problems. The **Release Notes** have ALL the information about the Intel graphics issues. People should read that before considering to upgrade.
It's there for a reason
 :rolleyes:

---

### Post by rohit2412 on 2009-04-30
@skymera

11 seconds boot...thats too gud...
how??

even my clean install took 17 seconds to login screen...
.......

---

### Post by mb_webguy on 2009-04-30
> **El Zoido said:**
> 9.04 is working quite nice for me, no major issues here.
I only encountered some minor oddities that could be resolved easly.
Boot-time has improved quite a lot for me.

Some of the issues I still have are with fullscreen video in totem (is working, but OSD is behaving strange) and VLC (bug, no OSD) and Flash performance ( I switched to 64bit, which still seems to have some issues with flash; nothing major though for me)

You can get a fixed version of VLC from [this PPA]("https://launchpad.net/~medigeek/+archive/ppa").  With that version, the OSD in fullscreen works just fine, and you can embed the video into the player.

As far as Flash on 64-bit, try uninstalling all Flash plugins from the repositories, as well as anything remotely Flash-related left on your system afterward.  Then download the [official plugin]("http://labs.adobe.com/downloads/flashplayer10.html") from Adobe and drop it into the /usr/lib/mozilla/plugins/ directory.  I had problems with the repository version, but after I did the above, Flash has worked beautifully.

---

### Post by krnekhelesh on 2009-04-30
Hi, I'm presently running Ubuntu 8.04, and I've been eagerly waiting to upgrade to Ubuntu 9.04. However my laptop uses a Intel Graphics Card and I read a lot of user's comments that there are preformance issues with the graphics card drivers.

Is there a workaround such that if I install ubuntu 9.04 would use the ubuntu 8.10 graphic card drivers?

---

### Post by El Zoido on 2009-04-30
> **mb_webguy said:**
> You can get a fixed version of VLC from [this PPA]("https://launchpad.net/~medigeek/+archive/ppa").  With that version, the OSD in fullscreen works just fine, and you can embed the video into the player.

As far as Flash on 64-bit, try uninstalling all Flash plugins from the repositories, as well as anything remotely Flash-related left on your system afterward.  Then download the [official plugin]("http://labs.adobe.com/downloads/flashplayer10.html") from Adobe and drop it into the /usr/lib/mozilla/plugins/ directory.  I had problems with the repository version, but after I did the above, Flash has worked beautifully.

Thanks for the advice, I already heard about it, but so far I've been too lazy :D ;)
Anyway Flash is working mostly fine for me, only occasionally Firefox will lock up for a couple of seconds on Flash-heavy sites.

---

### Post by DeMus on 2009-04-30
I've got it all working and it works fine. I feel it works faster than Hardy, and I don't only mean starting up since the computer runs 24/7 on 100%.
I did do a fresh install since I know upgrading from a previous version always gives problems. No matter which system you use, upgrading is always a bad idea. And it proves I'm right since most of the problems you read about here in the forum are related to upgrades.

---

### Post by LuigiAntoniol on 2009-04-30
When I installed the beta version, I hated it.

Now that I have the official release, I'm pleasantly surprised.  It is much faster on my PC than 8.10 was.  No problems with sound and video.

Only glitch is the NVIDIA proprietary drivers won't install, so I can't get Compiz to function.

Otherwise, everything else works beautifully.  I'd give Jaunty a 9.5/10. :)

---

### Post by cronos on 2009-04-30
Well, it seems the last time I used Ubuntu (or Linux) was during late 2007, because I went back to using Windows after something went wrong with my Ubuntu setup.

Anyway, I decided to install 9.04, and I have to say that I am very impressed with Ubuntu, and I hope I keep using it as my main OS.

---

### Post by shrndegruv on 2009-04-30
I like it. 

Except for the fact that my computer is unusable with it.

This is mostly due to the fact that I no longer have driver support for my ATI card.  The fglrx driver doesn't cut it due to 3 second lags for resizing/minimizing windows and crashing on alt tab.  The open source driver doesn't cut it because my computer becomes as hot as flame.  So I have no options.  

I know that the closed driver not working is ATIs fault, but what I would have expected from Ubuntu would have been a warning in big bold blinking letters not to upgrade if you have an ATI card.  I can't believe that in the six alpha/beta releases noone noticed that most ATI cards are unusable.

I am going to have to go back to windows....

---

### Post by El Zoido on 2009-04-30
Or you could just reinstall 8.10...
Or wait until ATI fixes their driver.

---

### Post by shrndegruv on 2009-04-30
My problem is more with the explicit lack of clear warning that ATI cards are unusable in jaunty.  

And the fact that there is no support for laptop hibernate/sleep functionality for ATI.  Laptops have been around long enough that I would think that functionality would be there.  It just doesn't work.  

this really isn't a viable solution for people that need all aspects of their hardware to work.

---

### Post by fjgaude on 2009-04-30
With me and upgrades, it's two steps forward, one back!

---

### Post by bengb on 2009-05-03
9.4 - have same problems w/Intel integrated graphics - have network issues too - still trying to work through though but am getting very frustrated w/ a sys that supposedly "just works".  Due to graphics and network issues, am unable to use computer for anything other than most basic and simple things - is definitely not ready for "Prime Time".

---

### Post by pbpersson on 2009-05-03
> **shrndegruv said:**
>  crashing on alt tab.  

I just went over to my Jaunty machine and tried an alt-tab.  It does not crash my machine, but it only shows one application and I have five open.

Now I know at least one thing to look for before I upgrade my production machine.

:)

---

### Post by clhsharky on 2009-05-03
9.04 has been a real treat this time around. Fast and every thing worked.
AMD processor and chips with ATI card.

---

### Post by nandemonai on 2009-05-03
> **muhannadfa said:**
> srry guys,
jaunty is buggy release
full of performance problem issues
if u cann't watch video's on OS what the heck
workaround they're talking about s not officail, and u can see, one saying working for me 10 saying nah! doesn't work
if u gonna try all the workarounds till u find the one it'll ineffective, which is not good
keep with 8.10, jaunty doesn't worth it till now, 
my advice wait for 9.10 > hope it's good
------------------------
issues with intel
issues with Nvidia
issues with ATI
issues with networking and routers
issues with Cpy over usage
>>>>>>> much much more<<<<<<<<<
------------------------------
that's my opinion

Nvidia working fine here, NM applet finally has fixed the annoying static bug and networking is running fine here. Experiences vary I guess.

---

### Post by charleskw on 2009-05-03
> **Anxious Nut said:**
> Thanks for the replies:)

but I've heard that 9.4 has some issues with Intel graphics or some thing like that! is that true?

yes... it's true

---

### Post by fjgaude on 2009-05-04
nVidia graphics works fine here, but cut-copy-paste to and from VMware virtual Windows OS does not! I wait to see if it gets fixed before using 9.04 as main OS.

---

### Post by moleculeman on 2009-05-10
After hating it yesterday, I've just about got things back to how I like them.
The big nuisance is that Amarok 2 is, as far as I can see, not as good (or I don't like it as much) as 1.4.

---

