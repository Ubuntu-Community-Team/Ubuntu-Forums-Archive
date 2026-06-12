---
title: "Any way to speed up OpenGL?"
date: 2009-10-30
forum: Gaming &amp; Leisure
---

### Post by dopefish7590 on 2009-10-30
I currently have Ubuntu 9.04 installed, and OpenGL is very sluggish, it has a hard time rendering glxgears at a decent speed when maximized (About 10FPS), much less any 3D game. I'm not sure what is wrong here, I have a small card, yes (32 MB), but it still worked a TON better in Windows. (I was able to play Open Source games that I can't now without lag, like Kiki the nanobot or Sauerbraten.) And running games with the lowest requirements is a nightmare on WINE. (SiN 1, for example.) Anyone know of any way to speed up OpenGL?

---

### Post by Sindwiller on 2009-10-30
> **dopefish7590 said:**
> I currently have Ubuntu 9.04 installed, and OpenGL is very sluggish, it has a hard time rendering glxgears at a decent speed when maximized (About 10FPS), much less any 3D game. I'm not sure what is wrong here, I have a small card, yes (32 MB), but it still worked a TON better in Windows. (I was able to play Open Source games that I can't now without lag, like Kiki the nanobot or Sauerbraten.) And running games with the lowest requirements is a nightmare on WINE. (SiN 1, for example.) Anyone know of any way to speed up OpenGL?

Glxgears is **not**, I repeat, **not** a benchmark. Neither does it demonstrate the performance of your graphics card, nor does it demonstrate the feature set of the graphics chip. Have you tried running Sauerbraten with the lowest settings? Perhaps set by console?

```
./sauerbraten -w1024 -h768 -b8 -z8 -a0 -f
```

> I have a small card, yes (32 MB)

a) The memory of a graphics card often isn't the only thing that determinates performance and compatibility. A "small graphics card" isn't really a useful expression.

b) Do you **know** what kind of graphics card or integrated chipset that is? Maybe you're running the open source drivers for your card, which mostly lack decent OpenGL support and performance. State what driver and graphics card you're running first.

PS. Jesus. It has come to my attention that nobody here feels bothered to elaborate his/her problem decently. Back when I started with Linux (4 years ago I think), everyone told me "Elaborate your problem, explain what you've done before, tell what hardware you're running, paste console output". What has happened to that?

---

### Post by dopefish7590 on 2009-10-30
Ah, I apologize for not elaborating... But I figured there were some non-driver specific options available because I *really* don't want to mess around with the drivers again, it was a nightmare getting it to work in the first place. I didn't think people would get angry.

My video card is a 32 MB ATI Radeon card on AGP, it doesn't really say anything else on the card about what it is. :\

I am *NOT* using the proprietary drivers (I have tried them, and they screwed up xorg.conf and even after replacing it with a backed up copy, X still wouldn't work) I suppose that's where my problem is.

Oh, and yes, I have tried minimal graphics settings for all the 3D programs I have tried.

---

### Post by Sindwiller on 2009-10-30
Ah, I see. Another case of the ATI flu.

It's a known.. uuh, problem that ATI's proprietary drivers are horrible. The GPL drivers on the other hand didn't have the advantage of being written by people who exactly know the interface and the circuit boards :S Apparently, the new mainline 2.6.32(?) Kernel (not completely stable AFAIK) features some updates on the GPL ATI drivers, but I don't know what or whether it might be useful for you.

Obviously, someone with more experience with ATI cards (I'm running a nVidia and I'm not switching) might help you to set the horrible proprietary drivers up if they don't work "out of the box" for you. The thing is that everything is depending on the OpenGL implementation and the interface in the drivers.

---

### Post by dopefish7590 on 2009-10-30
Alright. So I guess there isn't a lot I can do except a lot of trial and error with the ATI drivers huh? :s

Edit: A little bit of poking around revealed my graphics card is an ATI Radeon 7000/VE

---

### Post by del_diablo on 2009-10-30
> Edit: A little bit of poking around revealed my graphics card is an ATI Radeon 7000/VE

Dropped quite some time ago, but the open driver should work. 
BUT you need to manually set the xorg.conf i guess to get proper performance.
Lets se, i get this ideas on the top of my head:
*Driconf
*[http://wiki.archlinux.org/index.php/ATI#Configuration](http://wiki.archlinux.org/index.php/ATI#Configuration) (configuration of the xorg)

With a so old card i guess there is not much that is actually done with the open drivers, so upgrading would likely not give out more performance.

---

### Post by Sindwiller on 2009-10-30
Another light of hope might come from old, archived proprietary drivers on the side of ATI.

Maybe your performance bottleneck is caused by not having the X11 dri and drm modules loaded (as shown in the guide posted by del_diablo); after all, who knows.

---

### Post by handy on 2009-10-30
**@dopefish:** Have a look at the threads linked below, they will give you some background on what it currently going on with ATi GPU support, including where it is heading.

You are using the open-source drivers which currently offer the best 2D support for most ATi GPUs, but 3D is only starting to happen.

Anyway I won't repeat myself here, have a look at these two if you are interested:

[http://ubuntuforums.org/showpost.php?p=8198659&postcount=9](http://ubuntuforums.org/showpost.php?p=8198659&postcount=9)

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

---

### Post by del_diablo on 2009-10-30
> **handy said:**
> **@dopefish:** Have a look at the threads linked below, they will give you some background on what it currently going on with ATi GPU support, including where it is heading.

You are using the open-source drivers which currently offer the best 2D support for most ATi GPUs, but 3D is only starting to happen.

Anyway I won't repeat myself here, have a look at these two if you are interested:

[http://ubuntuforums.org/showpost.php?p=8198659&postcount=9](http://ubuntuforums.org/showpost.php?p=8198659&postcount=9)

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

Don't attempt to flood the tread. I suggest you read it as its really short at the moment, its not the "bleeding edge card" we are talking about but a really dated Radeon 7000.
3D has happend ages ago, there is full acceleration on the older cards.
"Current" is also irrelevant to the tread.

---

### Post by cascade9 on 2009-10-30
LOL @ del_diablo. You think that Handy made a useless post, so your quoted it in full, even though it was right above your post? With no info to help at all? That was _even_more_useless :P 

@ dopefish7590- this may help you out-

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Pity that ATI never relased linux drivers for the R100 chips. The RV100 (7000/VE) is a cut down R100 (7200) with no hardware T&L. I wouldnt be suprised if a 2nd hand $10 PCI card would get much better 3D performance.

---

### Post by handy on 2009-10-30
> **del_diablo said:**
> 
Don't attempt to flood the tread. I suggest you read it as its really short at the moment, its not the "bleeding edge card" we are talking about but a really dated Radeon 7000. 

Thanks for your kind words of support. :p

> **del_diablo said:**
> 
3D has happend ages ago, there is full acceleration on the older cards. 

Perhaps...

> **del_diablo said:**
> 
"Current" is also irrelevant to the t[h]read.

In your opinion apparently.

To recapitulate; there are a huge amount of changes happening regarding the open-source drivers, to the point that there will eventually be no drivers other than the kernel & Mesa.  There will also be no need for the (in the case of the ATi GPUs) proprietary Catalyst driver, as it will be inferior to the far more easily updated GNU/FOSS system that is currently being implemented.

There are a number of links to resources in the OP of the 2nd thread linked to, in my previous post.  Here it is again for anyone interested:

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

Some of these links are particularly pertinent with regard to what ATi chipsets are supported & how they are & will be.

Some people may find that & the other links particularly interesting. :) 

> **cascade9 said:**
> 
LOL @ del_diablo. You think that Handy made a useless post, so your quoted it in full, even though it was right above your post? With no info to help at all? That was _even_more_useless :P 

& wasted more space because his rudeness/thoughtlessness provoked what will turn out to be an even longer response from me! :lolflag:

> **cascade9 said:**
> 
@ dopefish7590- this may help you out-

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Pity that ATI never relased linux drivers for the R100 chips. The RV100 (7000/VE) is a cut down R100 (7200) with no hardware T&L. I wouldnt be suprised if a 2nd hand $10 PCI card would get much better 3D performance.

Perhaps the new system that is being implemented will cover the driver problem you mentioned.

Also, at a glance, I'm not too sure that the info' on the link you posted is completely accurate.

& it is fortunately becoming more inaccurate every day. :)

Overall, my posts should inspire some hope in people that have been putting up with the past inconsistent support from AMD/ATi, in combination with the very incomplete support from the open-source community.

This situation IS changing for the better.

---

### Post by dopefish7590 on 2009-10-31
Hey, thank you all for the help. I'll report back how things go. :)

---

### Post by cascade9 on 2009-10-31
> **handy said:**
> Also, at a glance, I'm not too sure that the info' on the link you posted is completely accurate.

& it is fortunately becoming more inaccurate every day. :)

Overall, my posts should inspire some hope in people that have been putting up with the past inconsistent support from AMD/ATi, in combination with the very incomplete support from the open-source community.

This situation IS changing for the better.

It probably isnt accurate with the newer ATI cards, but the old R100 it probably is. AFAIK, ATI never really supported the R100s under linux, and the RV100 being an oddball, cutdown card theres even less chance ATI is goign to bother making drivers for it. From checking the ATI site I would guess that they arent going to be doing much for cards from before the 8500. 

BTW, I will have to shove the old 9600 thats hanging aroudn here into a test system, just to see how much things have improved. I would really, really really like to see somebody fix the video card driver issues, and if ATI does, I'll change from nVidia to ATI from now on. Vote with my wallet :D

---

### Post by handy on 2009-10-31
> **cascade9 said:**
> 
BTW, I will have to shove the old 9600 thats hanging aroudn here into a test system, just to see how much things have improved. I would really, really really like to see somebody fix the video card driver issues, and if ATI does, I'll change from nVidia to ATI from now on. Vote with my wallet :D

AMD/ATi are helping with some tech' info', though it is my understanding that it is the GNU/FOSS people that have designed the new system & are implementing it.

The following is from a post in the Arch forums, which is good for getting an overview of what is going on & planned:


[I]1) Kernel mode setting on <R500 (Linux Kernel 2.6.31/Mesa 7.6) : DONE
2) &#922;ernel mode setting and 3D on >R500 (Linux Kernel 2.6.32 / Mesa 7.7) : Done by January 2010

(and in the future)

3) 2D support for R8xx (still no specifications) : Maybe March 2010
4) 3D support for R600/R700 ) (it's going to happen in .32) : By January 2010
5) Hardware calls through KMS and AtomBIOS : By March or maybe January 2010
6) Powersaving through KMS and on the fly switching on/off (there are patches waiting for going on drm-2.6) : By March/April/May we are gonna have sufficient powersaving through KMS for <R5xx
7) Gallium3D 3d/networking integration (no idea how it's going to happen)
8) Leaving support for radeon and radeonhd, and have 3D without them. I don't know how it's going to happen, but it's underway. : Maybe by the end of 2010, or by the first months of 2011
9) KMS and 3D support &#947;&#953;&#945; R8xx: By the end of 2010, or earlier if the code is not gonna be so much different.


Note: Except for 1 and 2, all the other dates are personal estimations.

Last edited by **flamelab** (2009-09-18 04:11:26)[/I]

---

