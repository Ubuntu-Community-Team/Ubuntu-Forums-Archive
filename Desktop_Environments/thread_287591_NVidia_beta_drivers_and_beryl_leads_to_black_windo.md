---
title: "NVidia beta drivers and beryl leads to black windows under gnome"
date: 2006-10-29
forum: Desktop Environments
---

### Post by drinkingbird on 2006-10-29
I've installed the nvidia beta drivers and beryl under edgy (using [this guide]("http://www.ubuntuforums.org/showthread.php?t=263851")), and while beryl seems to start up properly, I get a black desktop background, and most windows opened come up black as well.

Apparently this is a bug in the nvidia beta drivers in managing texture memory.

Does anyone know about the status of this bug, and whether there is a fixed version of the drivers?

Is there a workaround at all, possibly using the stable drivers or some such?

For reference, my video card is an nvidia GeForce FX Go5200 32M, and gnome seems to work fine with the beta nvidia drivers when beryl isn't running.

---

### Post by Julolidine on 2006-10-29
Nvidia has identified it as a problem as per 

[http://www.nvnews.net/vbulletin/showthread.php?t=77248&highlight=black+windows](http://www.nvnews.net/vbulletin/showthread.php?t=77248&highlight=black+windows)

however, there doesn't seem to be a workaround as of now.

---

### Post by ajm2005 on 2006-10-29
I get this effect with my nvidia 6200TC. It only has 64 Mb memory I think (the rest comes from memory shared from the system).


At the moment, the only way past the problem is to buy a new graphics card. :) Preferably one with plenty of onboard memory (one that doesn't rely on shared memory).

---

### Post by toma222 on 2006-10-29
Hi,

I have black windows and desktop too with both my Geforce 2MX 32Mb and my Geforce 4 Ti 64 Mb (only black windows on it). For the desktop, simply reload it fix it (for example under Gnome with nautilus -q).

One thing I don't understand is that the black windows doesn't appear with compiz-freedesktop with those beta drivers. So it is really a driver issue ?

(Sorry for my English, I'm French).

---

### Post by Julolidine on 2006-10-29
yeah, the shared memory seems to be the biggest issue.  My computer at work has 64MB video ram on an *old* NVidia card, and it still works brilliantly.  My laptop at home can't open more than one window...

Bah!  Oh well, I guess if thats my only problem upgrading to Edgy, I'm in good shape compared to some people.

---

### Post by Julolidine on 2006-10-29
> **toma222 said:**
> 
One thing I don't understand is that the black windows doesn't appear with compiz-freedesktop with those beta drivers. So it is really a driver issue ?

(Sorry for my English, I'm French).

Weird that the bug doesn't show up with compiz-freedesktop.  

Don't worry, your English is better than my French.  :mrgreen:   You'll be amazed how quickly your English will improve if you read the forums regularly and try to reply.

---

### Post by toma222 on 2006-10-29
Thanks.

I read it a lot and I try to reply when I can (and when I don't find my answers on the French forums).

This bug is very annoying and I'd like to understand it. Compiz-freedesktop is not really smooth and complete compared to Beryl.

---

### Post by ajm2005 on 2006-10-29
what's a good, cheap graphics card that is known to work well with beryl/ compiz? is nvidia preferred over ati? how much onboard memory should the card have preferably?

---

### Post by drinkingbird on 2006-10-30
> **ajm2005 said:**
> I get this effect with my nvidia 6200TC. It only has 64 Mb memory I think (the rest comes from memory shared from the system).


At the moment, the only way past the problem is to buy a new graphics card. :) Preferably one with plenty of onboard memory (one that doesn't rely on shared memory).

Hmm, not so easy with a laptop. The fact that the 32M video memory is supporting 1400x1050 resolution isn't really helping things either.

It's been years since I had a major problem with graphics drivers under linux, ahh the late nights spent trying to find the right set of configuration and animal sacrifice that would get X running in the late 90s :rolleyes:

---

### Post by Julolidine on 2006-10-30
This will force AIGLX rather than the NVidia Beta drivers.  Its a bit slower, but no black screen :-D .  

From terminal (of course shut down beryl and beryl-manager first)

```
beryl --use-cow --force-aiglx
```

Soooooooo I guess for the time being its the way to go.

---

### Post by toma222 on 2006-10-30
With my poor 1800+ 512Mb Geforce 2 MX it's very slow with this option (with high cpu usage).

And I have :
```
beryl: pixmap 0x3e000fc can't be bound to texture
beryl: Couldn't bind redirected window 0xc2c8b8 to texture
```

With compiz-freedesktop (from : [http://gandalfn.wordpress.com/]("http://gandalfn.wordpress.com/")) it's faster but slower than with Beryl.

---

### Post by HoMe_CaNiBaL on 2006-10-30
Hi.

i have that problem with nvidia beta drivers.so i install envy program to uninstall nvidia beta drivers, and install official driver (8774), but beryl, after that, wont start.

how i cant put beryl working again?

i have edgy, with p4 2.8 1gb ram and a 6600gt agp 128mb.

thks

oh sorry my english,i'm portuguese lol

---

### Post by highneko on 2006-11-09
> **Julolidine said:**
> This will force AIGLX rather than the NVidia Beta drivers.  Its a bit slower, but no black screen :-D .  

From terminal (of course shut down beryl and beryl-manager first)

```
beryl --use-cow --force-aiglx
```

Soooooooo I guess for the time being its the way to go.

Thank you very much, I've been looking everywhere! This's great.

---

### Post by mannheim on 2006-11-09
> **ajm2005 said:**
> what's a good, cheap graphics card that is known to work well with beryl/ compiz? is nvidia preferred over ati? how much onboard memory should the card have preferably?

My nvidia card has 256 MB. I can open up about 20 full-screen firefox windows (all empty) before hitting the black-screen-bug.

The actual card is not the fastest: a geforce 6200 with 256 MB. eVGA make this card without a fan, so its silent: that's the reason I chose it. It costs about $60 on Amazon in the US. I haven't anything to compare it to for speed, but it seems fast enough for beryl for my purposes.

---

### Post by kimro on 2006-12-08
I have a 6600GT 128mb edition and am getting black screen on full size at time..

---

### Post by net-x on 2006-12-08
I have the same problem too. :-k I solve it by this way: Minimize all windows on desktop, and un-minimize black window after.:mrgreen:

---

### Post by kimro on 2006-12-10
Does anyone have real fix for this issue?

---

### Post by H3g3m0n on 2006-12-22
"If opening multiple windows leaves some as black, you do not have enough video memory. This is a bug in the beta drivers - currently, shared video RAM cannot be used with the GLX_EXT_TEXTURE_FROM_PIXMAP extension. nVidia are aware of it, and it may be fixed in the future. In the meantime, one solution is to use the Copy rendering path - it can be enabled in beryl-manager (Advanced Beryl Options->Rendering Path)." from [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA)

I also hit the bug and i have a 7600 GT, I have a 1920x1200 widescreen and a habit of opening tons of windows so it chews up the memory fairly fast.

---

### Post by jonah1980 on 2007-01-06
take a look at this one: [http://www.ubuntuforums.org/showthread.php?t=295689](http://www.ubuntuforums.org/showthread.php?t=295689)

---

### Post by suhaib on 2007-01-25
I came across a guide somewhere which instructed me to create a new XGL session in which Beryl would run.  I can't find it any more :(

The only downside is that when I clicked shut-down, I could only log off, lock screen or switch user.  Or I could punch in ```
shutdown -r now
``` on the command line.

---

### Post by JamieC on 2007-01-25
> **suhaib said:**
> I came across a guide somewhere which instructed me to create a new XGL session in which Beryl would run.  I can't find it any more :(

The only downside is that when I clicked shut-down, I could only log off, lock screen or switch user.  Or I could punch in ```
shutdown -r now
``` on the command line.

It was probably [this](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL) guide (which also tells you how to import shutdown and restart functionality into to a XGL session)

---

### Post by blackdevil on 2007-05-23
> **H3g3m0n said:**
> "In the meantime, one solution is to use the Copy rendering path - it can be enabled in beryl-manager (Advanced Beryl Options->Rendering Path)." from [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA)

I also hit the bug and i have a 7600 GT, I have a 1920x1200 widescreen and a habit of opening tons of windows so it chews up the memory fairly fast.

Sweet that works for me. Does this decrease performance or anything? What are the implications of using Copy?

---

### Post by jonah1980 on 2007-05-23
Hi guys, is there any word on if this bug will ever be fixed, or do nvidia just not care about it..?

---

