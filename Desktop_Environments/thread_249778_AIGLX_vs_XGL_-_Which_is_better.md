---
title: "AIGLX vs XGL - Which is better?"
date: 2006-09-03
forum: Desktop Environments
---

### Post by mobilehavoc on 2006-09-03
Bit of a Linux noob but getting the hang of things gradually. I have XGL/Compiz working PERFECTLY on my Dapper Drake install - when I mean perfectly I'm not joking either..everything works smoothly and flawlessly.

I've been reading the forums a lot and noticed AIGLX being thrown around a lot and was curious if someone could briefly explain the advantages if any of AIGLX over XGL? Also if AIGLX is definitely the way to go is there a simple way without totally F'ing up my system to migrate from XGL/Compiz to AIGLX/Compiz?

Just curious - thanks for your help in advance.8)

---

### Post by Uncle Spellbinder on 2006-09-03
My understanding is that AIGLX works best with Intel Embedded Graphis such as mine. XGL did not work for me and AIGLX is completely wonderful!

---

### Post by mobilehavoc on 2006-09-03
I have an ATI X800XL so I'm assuming from your post that I should stick with XGL over AIGLX?

---

### Post by Uncle Spellbinder on 2006-09-03
> **mobilehavoc said:**
> I have an ATI X800XL so I'm assuming from your post that I should stick with XGL over AIGLX?


> **mobilehavoc said:**
> ...I have XGL/Compiz working PERFECTLY on my Dapper Drake install - when I mean perfectly I'm not joking either..everything works smoothly and flawlessly.


A wise man once said..."If it ain't broke, don't fix it."

---

### Post by Lunar_Lamp on 2006-09-03
But a geek once said... "If you haven't broken it yet, you haven't tinkered enough." ;)

There seems to be a certain amount of cooperation between them (or cooperation was reported a while ago as happening), so hopefully for the end user the final consequences shouldn't matter eventually.  I would also say that if you have xgl working, and don't know why you want to change to aiglx, it's not probably not worth it.

---

### Post by Uncle Spellbinder on 2006-09-03
> **Lunar_Lamp said:**
> But a geek once said... "If you haven't broken it yet, you haven't tinkered enough." ;)

Classic. Simply CLASSIC!  :D

---

### Post by Ramses de Norre on 2006-09-03
AIGLX doesn't work on ati yet, there are new drivers needed for running AIGLX and there are only such drivers available for a number of intel chipsets at the moment.
So you'll need to wait for AIGLX on ati or nvidia.

---

### Post by mobilehavoc on 2006-09-03
> **Uncle Spellbinder said:**
> A wise man once said..."If it ain't broke, don't fix it."
Also if I had followed this thought process, I'd still be using Windows XP. :D

---

### Post by ButteBlues on 2006-09-03
> **Ramses de Norre said:**
> AIGLX doesn't work on ati yet, there are new drivers needed for running AIGLX and there are only such drivers available for a number of intel chipsets at the moment.
So you'll need to wait for AIGLX on ati or nvidia.
This is patently untrue.

XGL would NOT work on my ATI Mobility 7500, whereas, AIGLX works flawlessly.

---

### Post by Ramses de Norre on 2006-09-03
> **a simple façade said:**
> This is patently untrue.

XGL would NOT work on my ATI Mobility 7500, whereas, AIGLX works flawlessly.

Really? Ok I'm wrong then.. I'll have to inform myself again I guess..

---

### Post by ButteBlues on 2006-09-03
It may be you were thinking of the proprietary FGRLX drivers, which, afaik, do not work with AIGLX.

The ATI and open-source Radeon drivers, however, run swell on AIGLX.

---

### Post by Ramses de Norre on 2006-09-03
Ow really? And does that work better than fglrx + xgl? I know aiglx is a better method then xgl but the open source drivers don't have hardware rendering, do they?
So which is better then: fglrx + xgl or ati + aiglx ?

---

### Post by ButteBlues on 2006-09-03
That, I couldn't tell you.

All I do know is that the FGLRX drivers don't support my Mobility card, and finally, after much trouble, I found that AIGLX and ati runs perfectly on my card... though, 24 bit display is a little laggy. 16 bit is fine though.

---

### Post by Kilz on 2006-09-03
Just a question, does AIGLX provide something that XGL doesnt? Or do they do the same things but with different code? In other words, is there a feature that one has that the other doesnt?

---

### Post by mobilehavoc on 2006-09-05
> **Kilz said:**
> Just a question, does AIGLX provide something that XGL doesnt? Or do they do the same things but with different code? In other words, is there a feature that one has that the other doesnt?
That's what I've been trying to find out myself!! Hopefully someone who's used both or knows enough can answer. ](*,)

---

### Post by sefs on 2006-09-06
I read a comparison somewhere and the gist of it is that XGL requires two xservers (or something arcane like that) to be running while aiglx only had one xserver (or something so) running so the advantage was in over head or something like that.  The article I had seen was on digg a couple weeks back.  Maybe a search there can find it again.

---

### Post by mata_svada on 2006-09-06
Maybe you should read [http://en.wikipedia.org/wiki/AIGLX](http://en.wikipedia.org/wiki/AIGLX), [http://en.wikipedia.org/wiki/XGL](http://en.wikipedia.org/wiki/XGL) and  [http://www.freesoftwaremagazine.com/articles/accelerated_x](http://www.freesoftwaremagazine.com/articles/accelerated_x). Helped me a lot.

The thing is that Xgl basicly is a window running in an X-Server which acts like the X-Server. So it is not really a solution. AIGLX on the other hand is part of the X-Server which allows accelerated indirect GLX rendering (same thing XGL does).

---

### Post by brucevangeorge on 2006-09-06
Quick Question:

Do AIGLX and XGL use hardware acceleration to draw the desktop? Or do they just do those facy effects.. like cube and warp.. etc.

I'm looking for a way to get my GPU to draw the desktop and take the load off the cpu. Do I need XGL/AIGLX? Or will the proper drivers do the job?

---

### Post by brucevangeorge on 2006-09-06
bump

---

### Post by BlacKat_K on 2006-09-06
Ok guys i have a question,well many but only one for you :) I have an NVidia GeForce FX 5200 Ultra card and in the settings it gives a full page of into about GLX.What is that?

---

### Post by ronmarley1 on 2006-09-06
> **Uncle Spellbinder said:**
> My understanding is that AIGLX works best with Intel Embedded Graphis such as mine. XGL did not work for me and AIGLX is completely wonderful!
Ditto here.

---

### Post by Onos on 2006-09-10
My display is currently running Compiz+Xgl using the open source Radeon driver (GPU is a Radeon 9000/rv250).

The compostioning features work reasonably well, with a few odd bugs in rendering popping up at shutdown/logoff or when trying to play back movies with mplayer (simply... awful. Enough to make me switch back to Metacity).

Also, I think I borked up my configuration by trying to run that setup described on [http://www.compiz.net/viewtopic.php?id=389]("http://www.compiz.net/viewtopic.php?id=389") for making separate gdm logins for either setup: when I do switch back to Metacity, I often wind up cycling back through either a console login or the gdm login screen several times.

Is there a HOWTO for setting up  compiz + AIGLX with the open source Radeon driver without completely hosing up my system (or should I back up my important files once again and dig out the LiveCD once more?)

---

### Post by ButteBlues on 2006-09-10
Well, to hit AIGLX, you'd need to remove the gdm changes you made for XGL to run, etc.

After that, you should just need a couple xorg.conf edits and a gdm.conf-custom edit, along with package installs, to run AIGLX.

---

### Post by SishGupta on 2006-09-10
Straight up I would say that AIGLX is better, despite not having current driver support. 
People have said this before but I am going to restate it a bit:

The thing aobut XGL is that it seems to me that it is more of a "hack" than a proper solution. XGL is an x server on top of an x server. For my card, this leaves me with some problems. If I don't run compiz on top of XGL I don't see my desktop or panels. I don't think this problem happens to many other people. The positive side of this "hack" i've heard is that it doesnt rely on certain things. This is why it works with the open video drivers, Nvidias linux drivers, and Fglrx. I am not sure but i think the problem with xgl being a "hack" is that different cards will work very differently. Also OpenGL applications will not run as DRI is not available in the 2nd xserver.

AIGLX on the other hand, it applys one of the core concepts of xorg, which is extensibility. AIGLX is an xorg extension. The problem with this extension is that it requires a certain video driver extension that is currently only in the open source drivers and not in official drivers. Hopefully, soon nvidia and ati will include this extension in their upcoming driver releases. The good thing about AIGLX is proper implementation of an idea and one xserver. Also an advantage of having this proper implementation of compositing means that you have DRI free for OpenGL applications, where as on XGL you do not. On my card I am able to run AIGLX with out running compiz while having a useable system.
I think also ubuntu 6.10 will be using AIGLX and not XGL. I do not know much about this.

I could be wrong on any of the things that I have said, but this is the information that i have gathered from many many sites and compiled in my head.

My ATI Mobility 7500 (non fglrx compatible) runs both XGL and AIGLX, however XGL crashes easily and doesnt work with out compiz. I am currently running AIGLX w/o compiz. I don't run compiz full time because the shutdown menu won't show up with it.

Hope some of this info helps. A lot of people didn't answer the original posters question they just posted what works with what.

---

### Post by ButteBlues on 2006-09-10
> **SishGupta said:**
> 
I think also ubuntu 6.10 will be using AIGLX and not XGL. I do not know much about this.

AIGLX is included in and turned on by default in Xorg 7.1, which is part of Edgy.

> My ATI Mobility 7500 (non fglrx compatible) runs both XGL and AIGLX, however XGL crashes easily and doesnt work with out compiz. I am currently running AIGLX w/o compiz. I don't run compiz full time because the shutdown menu won't show up with it.

Hope some of this info helps. A lot of people didn't answer the original posters question they just posted what works with what.

Hell, I have the same card and I could ONLY get AIGLX to run. And it runs wonderfully.

---

### Post by horatiub on 2006-09-17
> **a simple façade said:**
> AIGLX is included in and turned on by default in Xorg 7.1, which is part of Edgy.



Hell, I have the same card and I could ONLY get AIGLX to run. And it runs wonderfully.

I'm still confused what compiz offers more when is ran with AIGLX.

What am I missing if I run AIGLX without compiz?

---

