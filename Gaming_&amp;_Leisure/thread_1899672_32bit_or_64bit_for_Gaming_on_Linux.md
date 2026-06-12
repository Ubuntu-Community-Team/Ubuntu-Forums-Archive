---
title: "32bit or 64bit for Gaming on Linux?"
date: 2011-12-24
forum: Gaming &amp; Leisure
---

### Post by wh33t on 2011-12-24
Hey guys,

** Preamble **

My new years resolution will be to try and not use any Microsoft software for a year and hopefully never again. I've toyed with Ubuntu for ages but have never bothered to take the time it takes to learn and master like I have Windows. 

Due to all of the corporate fiasco's that have occurred and come to public eye as of recently I want to do my part to help bring equality and fairness to the world in the small ways that I know we all can. I realize supporting enormous super corporations is what causes them to exist continually, so I now feel that it's a moral imperative that I learn to use Open Source and community oriented software and products and hopefully contribute to the project as well.

I'm also really interested in learning Arduino engineering for small automation projects around the home (huge Zeitgeist Movement supporter here!) in hopes of being able to create small demonstrations to show how open source technologies and automation can bring about abundance and a better world in general. I hear Linux and Arduino can get along quite well.

** Actual Question **

So my actual question... What version of Ubuntu should I be doing this with? I need to be able to play the odd game here and there (L4D2, TF2 mostly).

I know the latest version 11.10 (I think) resembles a tablet OS. Seeing how I'm gonna start fresh with Ubuntu again I don't mind trying it out, but I still want to tip the odds in my favour of being able to get Ubuntu to do what I need it do (all the stuff I do on Windows). 

So... 32bit? 64bit? LTS version?

** My Hardware **

Do I need to upgrade my gear to similar frame rate in these games?

MSI 870-G45 Motherboard
AMD Phenom II X4 810 
4GB Ram
ATI Radeon 4670, 1GB

Any other tips you'd like to share with me would be welcome as well. Happy Holidays!

---

### Post by oldrocker99 on 2011-12-24
You have all the hardware you need, and, even if you had an ancient (1998-2004);) computer, Lubuntu or Xubuntu (which are NOT tablet OS-oriented) would run just dandy.

I run 64-bit and game extensively. There are a handful of games that don't have 64-bit versions, but one can always download source code and build it oneself (it isn't hard to learn). Inasmuch as 64-bit GNU/Linux needs 64-bit-specific programs, 98+% of programs are available in 64-bit versions. For 32-bit games, that, for example, you run under wine, the ia32libs package provides very good compatibility.

...and don't hesitate to ask questions!

---

### Post by wh33t on 2011-12-24
> **oldrocker99 said:**
> You have all the hardware you need, and, even if you had an ancient (1998-2004);) computer, Lubuntu or Xubuntu (which are NOT tablet OS-oriented) would run just dandy.

I run 64-bit and game extensively. There are a handful of games that don't have 64-bit versions, but one can always download source code and build it oneself (it isn't hard to learn). Inasmuch as 64-bit GNU/Linux needs 64-bit-specific programs, 98+% of programs are available in 64-bit versions. For 32-bit games, that, for example, you run under wine, the ia32libs package provides very good compatibility.

...and don't hesitate to ask questions!

I think I will go with 10.04 LTS 64 bit then :D Thanks for your help. I'll report back.

---

### Post by HolgerB on 2011-12-24
Heya wh33t,

>So my actual question... What version of Ubuntu should I be doing this with? 
I would go for the most recent Ubuntu LTS which currently is 11.10.
If Unity does not drive your boat you can always try Xubuntu or Lubuntu. I couldn't get a hang on either Unity or Gnome 3. So I stick to XFCE for now.

>So... 32bit? 64bit? LTS version?
32 bit vs 64 bit is not a big issue here. 64 bit Linux often supports 32 bit Linux native apps very well since there are compability libs. Even with 32 bit Linux you can use more than 4GB of RAM when you have a PAE kernel. In the end it is not a big deal. The few benchmarks people drag out which "show" that 64 bit Linux is faster than 32 bit Linux are pretty specific and on an average desktop system I doubt anyone will notice it.

>I need to be able to play the odd game here and there (L4D2, TF2 mostly).
Gaming is an issue on Linux...always....

If you want to play L4D2 and TF2 on Ubuntu, then consider buying Crossover Games:
[http://www.codeweavers.com/products/cxgames/](http://www.codeweavers.com/products/cxgames/)

They do officially support both TF2 and L4D2:
[http://www.codeweavers.com/compatibility/browse/name/?app_id=6160](http://www.codeweavers.com/compatibility/browse/name/?app_id=6160)
[http://www.codeweavers.com/compatibility/browse/name/?app_id=3379](http://www.codeweavers.com/compatibility/browse/name/?app_id=3379)

The mayor issues with WINE, Windows games and esp. Steam is that compatibility can easily be broken by a simple update to STEAM.

>Do I need to upgrade my gear to similar frame rate in these games?
>ATI Radeon 4670, 1GB
Your graphic adapter could be causing issues. I have a HD4670 myself, and have good as well as bad experiences with this card. The open source driver for the card is pretty nice but not fast enough for more demanding games. The propritary driver (fglrx) is much faster but often more unstable than the NVidia counterpart. For gaming under Linux I would always suggest getting a pretty recent used card from the bay (e.g. 8800 GT / 9500GT / 9800GT). They will easily outperform the HD4670. I know because I just switched from my HD4670 to a NVidia 9500GT after first having issues with fglrx and being then disappointed by the radeon performance.

HTH,
D$

---

### Post by kaldor on 2011-12-24
Doing gaming on 64 bit Ubuntu with very few snags. I've always found a quick and easy fix to the problems I have, usually related to older games. 

I believe 64 bit might be a bit better with some 3d rendering, so I guess there might be a slight improvement in using 64 bit over 32 bit.

Your hardware seems fine. The ATI Radeon will probably work fine, but there are some possible issues with the proprietary drivers. Also, NVIDIA cards tend to be much better when doing WINE gaming. That said, I've been using a low-end Radeon HD 6450 with minimal issues on Quake 4, Urban Terror, and a couple of WINE games. You won't be able to get into much modern hardcore gaming on Linux due to the lack of titles, but if you're into the type of games available then you'll definitely be fine.

---

### Post by wh33t on 2011-12-24
> **kaldor said:**
> Doing gaming on 64 bit Ubuntu with very few snags. I've always found a quick and easy fix to the problems I have, usually related to older games. 

I believe 64 bit might be a bit better with some 3d rendering, so I guess there might be a slight improvement in using 64 bit over 32 bit.

Your hardware seems fine. The ATI Radeon will probably work fine, but there are some possible issues with the proprietary drivers. Also, NVIDIA cards tend to be much better when doing WINE gaming. That said, I've been using a low-end Radeon HD 6450 with minimal issues on Quake 4, Urban Terror, and a couple of WINE games. You won't be able to get into much modern hardcore gaming on Linux due to the lack of titles, but if you're into the type of games available then you'll definitely be fine.

Thanks for the replies guys. I'm on Ubu 10.043 LTS right now as we speak. What is my first step? Is there some kind of "Newbies guide to linux gaming" that you can suggest I take a look at?

---

### Post by HolgerB on 2011-12-24
> **wh33t said:**
> Thanks for the replies guys. I'm on Ubu 10.043 LTS right now as we speak. What is my first step? Is there some kind of "Newbies guide to linux gaming" that you can suggest I take a look at?
Well, since your main games are L4D2 and TF2 you might simply go out there !
Install the ATI / AMD propitary driver, install WINE and then try your games on your fresh Ubuntu installation ? :)

---

### Post by wh33t on 2011-12-24
> **HolgerB said:**
> Well, since your main games are L4D2 and TF2 you might simply go out there !
Install the ATI / AMD propitary driver, install WINE and then try your games on your fresh Ubuntu installation ? :)

I'm on it. I'll report back. <3

---

### Post by wh33t on 2011-12-24
Ok, I've got Wine installed now. I just configured it was well (pretty simple wow!). Now how do I install something? Can I just download an .exe file now and double click on it?

Nvm. This is a lot easier than I figured. I downloaded the Steam.msi and right click properties, set as executable and viola!

---

### Post by HolgerB on 2011-12-25
> **wh33t said:**
> Ok, I've got Wine installed now. I just configured it was well (pretty simple wow!). Now how do I install something? Can I just download an .exe file now and double click on it?

Nvm. This is a lot easier than I figured. I downloaded the Steam.msi and right click properties, set as executable and viola!
Ok, great...but do not forget to install the closed-source driver for your ATI card. Otherwise you will experience low 3D performance :)

---

### Post by wh33t on 2011-12-25
> **HolgerB said:**
> Ok, great...but do not forget to install the closed-source driver for your ATI card. Otherwise you will experience low 3D performance :)

I installed my ATI driver. I believe it's working correctly as I upped the animation level of Gnome and the wiggly window thingy was all smooth and such. 

With that said... Steam running on Wine is pretty slow. So slow in fact I can see the delay between me clicking on Steam menu options and actually seeing the results. Is there any way to tweak this sucker out? Maybe in the Wine config I am missing something?

---

### Post by doorknob60 on 2011-12-25
Steam itself is usually a little slow and glitchy in Wine. Just gotta deal with it I guess, but it still does what it needs to. Do the games run fine? Because that's what really matters.

---

### Post by wh33t on 2011-12-26
> **doorknob60 said:**
> Steam itself is usually a little slow and glitchy in Wine. Just gotta deal with it I guess, but it still does what it needs to. Do the games run fine? Because that's what really matters.

Steam ran really poorly. When I tried to launch Left 4 Dead 2, it would never actually load into the game. Just say that Steam was launching it and then that box would disappear. So I've removed Left 4 Dead 2 and now I'm gonna try "playonlinux" and give that a whirl.

---

### Post by Perfect Storm on 2011-12-26
I would suggest starting a support thread in our wine forum.

---

### Post by wh33t on 2011-12-26
> **Artificial Intelligence said:**
> I would suggest starting a support thread in our wine forum.

Thanks man. I'll do that if I can't figure out PlayOnLinux.

---

### Post by Brebs on 2011-12-26
> **wh33t said:**
> "Newbies guide to linux gaming"
The Linux kernel needs to be tweaked for responsiveness. It seems to be written with servers in mind, rather than desktops.

Here's [some tips](https://bbs.archlinux.org/viewtopic.php?pid=1002264#p1002264). Probably best for you to start with installing the [Liquorix kernel](https://www.google.com/search?q=ubuntu+liquorix+kernel).

Run games at a higher priority than 0.

---

### Post by HolgerB on 2011-12-26
> **wh33t said:**
> I installed my ATI driver. I believe it's working correctly as I upped the animation level of Gnome and the wiggly window thingy was all smooth and such. 
You can easily find out wether fglrx is installed or not by opening a terminal and typing the following command: glxinfo | grep OpenGL.

The message displayed then should state something like this:
```

OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: AMD Radeon HD 6300 series Graphics
OpenGL version string: 4.1.11005 Compatibility Profile Context
OpenGL shading language version string: 4.10

```

Of course with a different chip type then HD 6300.

As for Steam under WINE: It can beheave often quite flakey. 

Simply check out the Wine appDB for possible issues and fixes:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444)

---

### Post by WienerWuerstel on 2011-12-26
> **Brebs said:**
> The Linux kernel needs to be tweaked for responsiveness. It seems to be written with servers in mind, rather than desktops.

Here's [some tips]("https://bbs.archlinux.org/viewtopic.php?pid=1002264#p1002264"). Probably best for you to start with installing the [Liquorix kernel]("https://www.google.com/search?q=ubuntu+liquorix+kernel").

Run games at a higher priority than 0.

I highly doubt that this will make a difference at ALL

The standard Kernel is fast enough for the Desktop or do you have some Benchmarks that prove me wrong? :P

---

### Post by Brebs on 2011-12-26
> **WienerWuerstel said:**
> I highly doubt that this will make a difference at ALL
I have about 5 years of Linux gaming experience, experimenting with these settings and patches, then trying the results myself.

For example, the default mouse polling rate (125hz) is rubbish to me, after having tasted the smoothness of higher settings. I can *just about* tell the difference between 1000hz (what I use) and 500hz.

The benchmark I use is my own eyes, looking for average latency, and latency spikes.

Gaming is quite an extreme system test, for a multitasking OS. Ideally, we want to be able to run background stuff (e.g. compiling) while running a game, and not notice much additional latency in the game. To do that, the kernel/system must be tweaked to prefer low-latency rather than throughput, and use e.g. the **ionice** & **nice** commands (rather than relying on luck) to specify that the game takes priority, for both CPU & disks.

For benchmarks, I am reminded of the [Phoronix farce](http://ck-hack.blogspot.com/2011/08/phoronix-revisits-bfs.html). No trolling, please.

---

### Post by WienerWuerstel on 2011-12-26
> **Brebs said:**
> I have about 5 years of Linux gaming experience, experimenting with these settings and patches, then trying the results myself.

For example, the default mouse polling rate (125hz) is rubbish to me, after having tasted the smoothness of higher settings. I can *just about* tell the difference between 1000hz (what I use) and 500hz.

The benchmark I use is my own eyes, looking for average latency, and latency spikes.

Gaming is quite an extreme system test, for a multitasking OS. Ideally, we want to be able to run background stuff (e.g. compiling) while running a game, and not notice much additional latency in the game. To do that, the kernel/system must be tweaked to prefer low-latency rather than throughput, and use e.g. the **ionice** & **nice** commands (rather than relying on luck) to specify that the game takes priority, for both CPU & disks.

For benchmarks, I am reminded of the [Phoronix farce]("http://ck-hack.blogspot.com/2011/08/phoronix-revisits-bfs.html"). No trolling, please.

That's YOUR preference then but the OP won't need any Kernel Patches that may or may not make a Game *faster*.

And my experience is that most People only have the Game running while playing said Game. Because who needs 1000 extra things running in the Background when they play? A Console doesn't and it's made for gaming.

But that's just my 2 Cents on it and not *trolling.*

---

