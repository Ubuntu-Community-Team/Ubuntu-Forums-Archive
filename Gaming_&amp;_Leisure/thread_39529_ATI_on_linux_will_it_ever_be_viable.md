---
title: "ATI on linux: will it ever be viable?"
date: 2005-06-05
forum: Gaming &amp; Leisure
---

### Post by Curlydave on 2005-06-05
What my understanding and from my experience, ATI cards and linux don't play together nicely. I'm getting terrible performance on my x800pro in Linux, a small fraction of what I get in Windows. From what I understand, the performance hit with Nvidia isn't as much.

Will Linux ever support ATI cards properly?

---

### Post by sard on 2005-06-05
ATI is definitely worse and despite the fine words from them nothing ever changes.  Have you tried other distributions as I get horrible performance with Ubuntu whatever manufacturer's card I have.

---

### Post by enquiry on 2005-06-05
[QUOTE=Curlydave]
Will Linux ever support ATI cards properly?[/QUOTE]
But you see, it's the other way around. GNU/Linux is not the problem, the problem is firstly that ATI haven't prioritised other operating systems than Windows, and secondly both their hardware and drivers are proprietary, so the community can't make drivers that works much better than the ones we have.

Unfortunately the official drivers will probably not become open source any time soon, even if ATI wanted it to, 'cause some of the technology is licensed by other companies. The good news is that ATI have made some welcome improvements to their proprietary driver recently (I think I have quite good 3D support, even compared to Windows), and they are apparently making an effort to improve it further.

---

### Post by slux on 2005-06-05
You can still either support the development of the free software drivers that are available ([http://r300.sf.net](http://r300.sf.net) and [http://dri.sf.net/](http://dri.sf.net/)) and buy an ATI that can be used with those or you can go to the [company that cares more about Linux support](http://www.nvidia.com/) even though their drivers are proprietary as well. Just vote with your wallet and stop complaining about things that are ATI's fault and not Linux's

---

### Post by meldroc on 2005-06-05
What can I say?  ATI's lack of good Linux support has cost them at least one customer.  Since they won't release programming information for their hardware, and won't create closed-source drivers that are a match for NVidia's, I'll go with NVidia every single time.

---

### Post by oritpro on 2005-06-05
I just ordered a new 6600GT to replace a 9800 Pro in one of my kids machines.  That leaves one down and one to go.

Games are going to be the only way I can get my kids on the Linux bandwagon and ATI's drivers just don't cut it.

---

### Post by Khannie on 2005-06-06
I just ditched my 9800 pro for a 6600GT. Using the default apt-get drivers for nvidia, I was beating the latest ATI drivers by 70% in glxgears. Absolutely astounded. Never buying ATI again.

---

### Post by az on 2005-06-06
I am not in the know on this but I do know that ATI makes a greater effort to release specs than nvidia.

In the long run, releasing the specs does more for Free-Libre open source software than releasing a closed-source proprietary driver.

I think in the future, ATI will come out on top as being more linux friendly than Nvidia.

---

### Post by skoal on 2005-06-06
I think it's merely a matter of time...

I remember early Nvidia Linux support - per chip drivers and minimal performance gain.  As they migrated to a unified driver framework, the Linux base flourished even more.

ATI doesn't need more (or better) programmers.  Hell, they don't even need a spiffy support forum.  What they need is direction.  Intel still holds a ~32% market share with ATI and Nvidia hovering around ~28%.  I think Nvidia is (and has been) investing in the future for some time now.  Not just on Linux either - Xbox anyone?  I think as far as corporate direction goes, ATI has always lagged behind Nvidia in that sense - Xbox2 anyone?  And then you have PCI express, etc.  Unfortunately, I think ATI is content with keeping it's Windows share and adventuring into new investments only once the profit has been proven viable.  That's just my analysis, and if correct, not the most reassuring.

\\//_

---

### Post by Khannie on 2005-06-07
Just ditched my 9800 pro for a 6600GT. The performance gain was /enormous/ (> 70%). Never buying ATI again as a result.

---

### Post by Khannie on 2005-06-07
[QUOTE=azz]I think in the future, ATI will come out on top as being more linux friendly than Nvidia.[/QUOTE]

To your average joe, all that matters is how well the drivers work (for me it's UT2004) and nvidia have made their name as being the linux kings in this regard. I think that it would be very difficult to turn that perception around.

I only have ubuntu installed a week and I got a 6600GT because I was horrified at how bad UT2k4 played with my 9800 pro in linux (did a card + cash swap with a mate). 30 minutes later and I knew I'd never be buying ATI again. 

The cards perform relatively closely in Windows, but the difference in performance in linux was nothing short of astounding.

---

### Post by slux on 2005-06-07
[QUOTE=azz]I am not in the know on this but I do know that ATI makes a greater effort to release specs than nvidia.

In the long run, releasing the specs does more for Free-Libre open source software than releasing a closed-source proprietary driver.

I think in the future, ATI will come out on top as being more linux friendly than Nvidia.[/QUOTE]

They released specs (or offered them under an NDA) up to the cards with the r200 core (the last one of which is Radeon 9250 with a r280). After that, with the r300 and upwards ATI hasn't made any specs available and the r300 driver that has been advancing lately is purely a reverse-engineering effort. ATI only offers their (poor) binary drivers today.

---

### Post by PaulX on 2005-06-07
I'm tired of hearing people bashing ATI for nothing. I use ATI proprietary drivers, and my UT2004 performance is hell better than on windows, and i have a nice windows setup, with even overclocked GPU on windows. All i had to do is recompile a kernel. I don't use a bleeding edge kerneel. I recompiled linux-2.6.10 from kernel.org and i patched it with ac patch and compiled it with compile options adequate for my machine. My card is a mobility 9600 radeon with 64 mb of RAM and i play UT2004 3335 version with all settings at high at 1280*800 resolution. That is more than decent

---

### Post by Curlydave on 2005-06-07
[QUOTE=PaulX]I'm tired of hearing people bashing ATI for nothing. I use ATI proprietary drivers, and my UT2004 performance is hell better than on windows, and i have a nice windows setup, with even overclocked GPU on windows. All i had to do is recompile a kernel. I don't use a bleeding edge kerneel. I recompiled linux-2.6.10 from kernel.org and i patched it with ac patch and compiled it with compile options adequate for my machine. My card is a mobility 9600 radeon with 64 mb of RAM and i play UT2004 3335 version with all settings at high at 1280*800 resolution. That is more than decent[/QUOTE]

So, how exactly did you pull that off? I'm getting piss-poor performance (20-40fps)with an X800 at that resolution, and that's without AA/AF etc. (Doesn't matter as noone knows how to do this.)

I know that you explained how you did it, but as a new user I don't understand; I just want to get performance like I do in Windows. How did you recompile the kernal, and why did that give you decent performance? Also, if you know how to turn on AA/AF/vsync/TB, I'd love to know.

---

### Post by oritpro on 2005-06-08
[QUOTE=PaulX]I'm tired of hearing people bashing ATI for nothing. I use ATI proprietary drivers, and my UT2004 performance is hell better than on windows, and i have a nice windows setup, with even overclocked GPU on windows. All i had to do is recompile a kernel. I don't use a bleeding edge kerneel. I recompiled linux-2.6.10 from kernel.org and i patched it with ac patch and compiled it with compile options adequate for my machine. My card is a mobility 9600 radeon with 64 mb of RAM and i play UT2004 3335 version with all settings at high at 1280*800 resolution. That is more than decent[/QUOTE]

I'd be interested in hearing how you did this as well.  I've been using Linux for several years now and have never had very good luck with ATI drivers. The Nvidia drivers just install and work with a minimum of effort.

I did get the ATI drivers working on one of my machines but UT2004 would just quit to the desktop after a few minutes with a segmentation fault.

Btw - what is the ac patch?

---

### Post by Frozen on 2005-06-08
im gonna have to side with PaulX on this 1 i think. im aware that nvidia have much better support for linux with their drivers. i have an ati 9700pro the MAYA II version from gigabyte. now im pretty new to linux and for tthe last few months ive switched between many different distro's and have had poor luck with ati drivers, however i switched to Kubuntu about a month ago (love it btw :D) and found a howto on these forums to install the most recent ati drivers and it works perfectly, installed and running in about 5 minutes. my scores in glxgears are around 4000 and in fgl_glxgears its around 800-900ish. now from what ive seen this is much lower than most nvidia owners but i can run doom3 and ut2004 at highest quality on 1024x768 (highest my moniter will go lol) perfectly, infact i honestly think that doom3 runs better in kubuntu than it did in windows, tho thats only from a glitch that i always noticed on the startup video in windows that is not there in linux.

---

### Post by brj on 2005-06-08
[QUOTE=Frozen]im gonna have to side with PaulX on this 1 i think. im aware that nvidia have much better support for linux with their drivers. i have an ati 9700pro the MAYA II version from gigabyte. now im pretty new to linux and for tthe last few months ive switched between many different distro's and have had poor luck with ati drivers, however i switched to Kubuntu about a month ago (love it btw :D) and found a howto on these forums to install the most recent ati drivers and it works perfectly, installed and running in about 5 minutes. my scores in glxgears are around 4000 and in fgl_glxgears its around 800-900ish. now from what ive seen this is much lower than most nvidia owners but i can run doom3 and ut2004 at highest quality on 1024x768 (highest my moniter will go lol) perfectly, infact i honestly think that doom3 runs better in kubuntu than it did in windows, tho thats only from a glitch that i always noticed on the startup video in windows that is not there in linux.[/QUOTE]
 do these new drivers also support the dvi output ?

jakob

---

### Post by Frozen on 2005-06-08
im not sure about the dvi output, though i believe the tv-out works, i have no idea if these two are related in any way, nor have i got tv-out setup at the present moment, however have had it working in past.

if you want i can search for my dvi adaptor and can try hooking up my moniter to that, let me know as it may involve a lot of searching and im rather lazy :D so wont look unless its needed hehe

Frozen

---

### Post by Curlydave on 2005-06-08
DVI's not an issue. I'm having tons of video issues, but a lack of DVI isn't one of them. I use DVI; I don't even think I have an analog VGA cable, but Linux has given me no trouble with that. This applies to the ATI and fglrx drivers.

---

### Post by PaulX on 2005-06-09
the segmentation fault will be solved by installing the loki 3355 patch for ut2004.
I downloaded 2.6.10 vanila sources. Downloaded ac12 patch. gzip -dc /where/the/patch/file.gzis | patch -p1
Make menucoonfig. COnfig that out. Compile and install. And than build the kernel module of fglrx. Reboot. You are done

---

### Post by brj on 2005-06-12
[QUOTE=Curlydave]DVI's not an issue. I'm having tons of video issues, but a lack of DVI isn't one of them. I use DVI; I don't even think I have an analog VGA cable, but Linux has given me no trouble with that. This applies to the ATI and fglrx drivers.[/QUOTE]

this is interesting. my radeon 9200 dvi-output goes black as soon as it switches to the graphics mode when i use the 'fglrx'-driver :(
this is not an issue with the 'ati'-driver. 

i'm neither a linux-crack nor a complete newbie, so i think it should be possible to install these drivers without the need to dig deep in the system. 

could you please post your xorg.conf ?

jakob

---

### Post by brj on 2005-06-12
[QUOTE=brj]this is interesting. my radeon 9200 dvi-output goes black as soon as it switches to the graphics mode when i use the 'fglrx'-driver :(
this is not an issue with the 'ati'-driver. 

i'm neither a linux-crack nor a complete newbie, so i think it should be possible to install these drivers without the need to dig deep in the system. 

could you please post your xorg.conf ?

jakob[/QUOTE]


the driver detects both outputs, but the primary (dvi) does not show a picture

...
(II) fglrx(0): Primary head:
 Monitor   -- TMDS
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- DVI_DDC
(II) fglrx(0): Secondary head:
 Monitor   -- CRT
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- VGA_DDC
...

---

### Post by joele on 2005-06-12
If you want to use cedega I would suggest using nividia cards not ATI as many games do not work with cedega since 4.x if you have an ATI card... 

I have Nvidia card in my desktop and ATI in my laptop and have been usin Linux for may years, ATI is just less compatable and involves more patches to get it to work. So to be honest if I was recommending a video card for someone using Linux I would have to recommend Nvidia simply as it will be less hassle for them...

---

### Post by Curlydave on 2005-06-12
[QUOTE=joele]If you want to use cedega I would suggest using nividia cards not ATI as many games do not work with cedega since 4.x if you have an ATI card... 

I have Nvidia card in my desktop and ATI in my laptop and have been usin Linux for may years, ATI is just less compatable and involves more patches to get it to work. So to be honest if I was recommending a video card for someone using Linux I would have to recommend Nvidia simply as it will be less hassle for them...[/QUOTE]

And you won't get shit frame rates. But I still wouldn't even bother with games on Linux at this point.

---

### Post by joele on 2005-06-12
[QUOTE=Curlydave]And you won't get shit frame rates. But I still wouldn't even bother with games on Linux at this point.[/QUOTE]

It depends on what you play, I only really play RTCW Enemy Territory frequently and it plays better on linux than windows, I would guess Doom3's linux binaries would work equally well?

---

### Post by Curlydave on 2005-06-13
[QUOTE=joele]It depends on what you play, I only really play RTCW Enemy Territory frequently and it plays better on linux than windows, I would guess Doom3's linux binaries would work equally well?[/QUOTE]

Hmm, I'll have to try that game on Linux. I used to play ETF all the time. I have indeed gotten Doom3 working on Linux, but I can't give you a confirmation as I'm using ATI. (x800). It certainly does not run anywhere close to equally well, but that's probably because of the ATI card. I can't say if an Nvidia card would give equal performance.

In addition to the performance reasons, I have run into many other problems ranging from annoyance to pain-in-the-ass wtih games. Eg: you can't minimize games unless you run them in a windows, Doom3's sound for me is really messed up, I can't get surround sound working or even my primary soundcard as long as onboard is enabled etc.

---

### Post by Ranime on 2005-06-15
Isn't it so that the framerate is immited to 60fps in Doom3, so the rest of te resources can be used to fill other needs in the game?

What about playing with an Ati-card... I Play Q3 and UT2k4 with mine (Ati9600/256MB) and it run nice in 1024*768. Most of the times i get between 89 and 260 fps. everything full detail...

Sure, it takes some tweaking in your xorg.conf... but what the heck! It's purring like a kitten :)

---

### Post by Curlydave on 2005-06-15
[QUOTE=Ranime]Isn't it so that the framerate is immited to 60fps in Doom3, so the rest of te resources can be used to fill other needs in the game?

What about playing with an Ati-card... I Play Q3 and UT2k4 with mine (Ati9600/256MB) and it run nice in 1024*768. Most of the times i get between 89 and 260 fps. everything full detail...

Sure, it takes some tweaking in your xorg.conf... but what the heck! It's purring like a kitten :)[/QUOTE]

It's limited to 60fps because that's what the engine runs at. You shouldn't really be getting much more fps than that anyhow as you're limited to your refresh rate, and vsync is a must. (I wish I could turn that on in Linux...) I'd imagine that 60-75fps with vsync would be alot smoother than 260 without.

---

### Post by PaulX on 2005-06-16
And remember, after XORG, very important is your kernel configuration. The same kernel that is stock on ubuntu, but compiled with march= -penitum-m  Doubled my framerates. BTW Try playing UT out of a window manager. KIll X and then go to the UT2004 folder and xinit ./ut2004.

I'm an ATI user and i will always be :grin:

---

