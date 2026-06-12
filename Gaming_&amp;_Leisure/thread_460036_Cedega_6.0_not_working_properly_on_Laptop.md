---
title: "Cedega 6.0 not working properly on Laptop"
date: 2007-05-31
forum: Gaming &amp; Leisure
---

### Post by cooler_inc on 2007-05-31
Hello!

I searched the forum and didn't find the answer

I have a laptop Samsung R40 K004 Cel.M 1.47/512/Ati RC200m 128Mb IGP Ubuntu 6.10
Installed driver ati-driver-installer-8.35.5-x86.x86_64.run as described [here]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

I can install and run games (FlatOut2, Painkiller), but it's slow down (about 2-3fps)

In the menu of FlatOut2 car rotates too slow and the game doesn't start (only music)

I tried to change engine to 5.2.1, but it didn't solve the problem

fgl_glrxgears show 1100frames and 210-220FPS

glxgears runs normal, but when I tried to run Video Test through the Cedega's interface - glxgears ran very very slow.

I've got the latest version of Wine, the problem is the same

Does anybody know hot to solve the problem?

---

### Post by EndPerform on 2007-05-31
Has Cedega ever run fast for you?  ATI cards usually don't have the best performance under Linux due to the drivers.  If Cedega has been pretty fast and now it's running slow, have you changed anything?

---

### Post by cooler_inc on 2007-05-31
Before I didn't run cedega because I had installed windows, and there these games worked fine

---

### Post by Prisma on 2007-05-31
> **cooler_inc said:**
> Hello!

I searched the forum and didn't find the answer

I have a laptop Samsung R40 K004 Cel.M 1.47/512/Ati RC200m 128Mb IGP Ubuntu 6.10
Installed driver ati-driver-installer-8.35.5-x86.x86_64.run as described [here]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

I can install and run games (FlatOut2, Painkiller), but it's slow down (about 2-3fps)

In the menu of FlatOut2 car rotates too slow and the game doesn't start (only music)

I tried to change engine to 5.2.1, but it didn't solve the problem

fgl_glrxgears show 1100frames and 210-220FPS

glxgears runs normal, but when I tried to run Video Test through the Cedega's interface - glxgears ran very very slow.

I've got the latest version of Wine, the problem is the same

Does anybody know hot to solve the problem?


Hey I had a similar problem with Guild Wars not detecting my video card, dont worry its actually easy to fix. All you have to do is to download and install the latest engine of cedega (the 6.1 engine) it works beautifully with Ubuntu).

---

### Post by lamalex on 2007-05-31
has cedega ever worked? use crossover [www.codeweavers.com](www.codeweavers.com). i get better FPS in linux than I ever did in windows with an ATI card.

---

### Post by cooler_inc on 2007-05-31
Ok I'll try cedega 6.1 and CrossOver
If anybody has some thoughts about this problem just post
See you on Thuesday

---

### Post by hikaricore on 2007-05-31
> **cooler_inc said:**
> Before I didn't run cedega _because I had installed windows_, and there these games worked fine

With a statement like that, normally I would point you in the direction of: [Linux is not Windows]("http://linux.oneandoneis2.org/LNW.htm")

But..Maybe you misunderstood the response by the community member above this post...
ATI drivers under linux are shotty at best, ATI has shown a complete lack of regard for the interests of the linux community and failed to make stable/proper drivers for most cards.

Also many of the games you listed use directx heavily.  While wine/cedega can process directx, it doesn't do it flawlessly, and this leads to slowdown.

If you have issues with Cedega I suggest contacting Cedega Technical support, or ask on their forums.
I'm not saying no one here will help with Cedega as that would be ignorant of me, but alot of folks around here don't take too kindly to Cedega's thievery.

---

### Post by Prisma on 2007-05-31
> **hikaricore said:**
> With a statement like that, normally I would point you in the direction of: [Linux is not Windows]("http://linux.oneandoneis2.org/LNW.htm")

But..Maybe you misunderstood the response by the community member above this post...
ATI drivers under linux are shotty at best, ATI has shown a complete lack of regard for the interests of the linux community and failed to make stable/proper drivers for most cards.

Also many of the games you listed use directx heavily.  While wine/cedega can process directx, it doesn't do it flawlessly, and this leads to slowdown.

If you have issues with Cedega I suggest contacting Cedega Technical support, or ask on their forums.
I'm not saying no one here will help with Cedega as that would be ignorant of me, but alot of folks around here don't take too kindly to Cedega's thievery.


Hey Hikaricore, take it easy man. Relax, Its completely reasonable that users want to run their windows games on Ubuntu specially when there is no Linux version available. I think is good for the Ubuntu community as a whole to support this kind of issues.  

I am 100% sure that AMD will release new outstanding ATI drivers in few months. Most likely they will go open source with Linux. They are the ones who are behind the open source project OLPC. I think they are also providing the graphic chip for those laptops. 

peace.

---

### Post by hikaricore on 2007-05-31
> **Prisma said:**
> Hey Hikaricore, take it easy man. Relax, Its completely reasonable that users want to run their windows games on Ubuntu specially when there is no Linux version available. I think is good for the Ubuntu community as a whole to support this kind of issues.  

I think you underestimate the issues Cedega causes for the linux community when it doesn't work.

As I said, there are people here who will help with Cedega based issues, but I'm not one of them.
I was suggesting the OP might have better luck asking on the transgaming forums than having to
deal with all of the folks like myself who nearly ignore Cedega's existance.

---

