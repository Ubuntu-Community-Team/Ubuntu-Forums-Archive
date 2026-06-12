---
title: "Nvidia - opengl"
date: 2005-12-05
forum: Gaming &amp; Leisure
---

### Post by alynx on 2005-12-05
Hi 

I have som lag problems when playing Wow in Ubuntu.
I was kinda wondering if someone could give me some hints or guides to get my Nvidia GFORCE 6600 GT to run with optimal OpenGL support ?

I use Wine 0.9.1 , and the game itself has no other error than the lagging:confused:

---

### Post by Zeroedout on 2005-12-05
There are a few things you can do. First off, I'de upgrade to wine 0.9.2. Next, Are you running an optimized kernel? You can try downloading the kernel more specific to your CPU. If you want to go to the next step, try compiling the kernel for your needs specifically, and use something like the nitro patchset to optimize it for performance. Though it probebly wont help performance, try prelinking your system, that'll help start up time, there is a really nice prelink how to in the forums. Also, make sure you have the latest driver.

---

### Post by bunced on 2005-12-05
The problem is the fact that you are running it through wine. Wine itself is a monolithic beast of software that slows down everything on the account that everything has to be run through a kind of emulator. You are never going to get Windows speed therefore. If you are serious about playing WOW in Linux, you could try Cedega ([http://www.transgaming.com/](http://www.transgaming.com/)) which is a heavily modified version of Wine geared towards gaming. It costs $3 for a minimum of three months but you do get very good quality support.

---

### Post by alynx on 2005-12-05
i think ill try all the free things first :) 

I have a FPS that varies from 40-60 when im in a low populated zone, checking in a high populated tomorrow! Ill try everything possible to get it to run smoother.

I got my nvidia driver by sudo apt-get install nvidia-glx 

Then i changed my xorg.conf from nv to nvidia.

Am i automaticly getting the latest and best driver ??

Anyhows , how and where do i get that if im not getting it by doing what i mentioned above ??

---

### Post by Zeroedout on 2005-12-05
[quote=bunced]The problem is the fact that you are running it through wine. Wine itself is a monolithic beast of software that slows down everything on the account that everything has to be run through a kind of emulator. You are never going to get Windows speed therefore. If you are serious about playing WOW in Linux, you could try Cedega ([http://www.transgaming.com/]("http://www.transgaming.com/")) which is a heavily modified version of Wine geared towards gaming. It costs $3 for a minimum of three months but you do get very good quality support.[/quote]
You are so misinformed that my head actually hurts! How the bloody hell did you come up with wine being a "monolithic beast of software," and that is emulates? Let's start with the word WINE ( Wine Is Not an Emulator). WINE re-implements the windows API (Application Programming Interface) on linux. That being said, there is no slow-down or speed gain because of WINE, unless the application you are running has been written by a brain dead monkey (that does happen once in a while). This page [http://winehq.com/site/myths](http://winehq.com/site/myths) will explain things much better than I can. Read it, for the love of god, read it! :) Moreover, WINE actually runs WOW and Half Life 2 better than cedega in most cases, or so I have heard. The DX9 patches in it are VERY good. As for cedega, it is a fork of wine, when wine was using a BSD license. The reason it is closed source is because they have agreements with the copy protection owners to have said copy protection in the cedega code (I think it was safe disc, but it may be something else). I'm sorry if I came off a little harsh, however, that was not my intention.

---

### Post by mcrosmar on 2005-12-06
[quote=alynx]Hi 

I have som lag problems when playing Wow in Ubuntu.
I was kinda wondering if someone could give me some hints or guides to get my Nvidia GFORCE 6600 GT to run with optimal OpenGL support ?

I use Wine 0.9.1 , and the game itself has no other error than the lagging:confused:[/quote] 
Have a look here [http://ubuntuforums.org/showthread.php?t=92367]("http://ubuntuforums.org/showthread.php?t=92367")
and here [https://wiki.ubuntu.com/WorldofWarcraftHowto]("https://wiki.ubuntu.com/WorldofWarcraftHowto")

I think that you'll find the answers.......

---

### Post by tkalfaoglu on 2011-06-20
Yep, he is very wrong.

When I dual boot to windows, I get 40 FPS in WOW. When I use it under wine (fedora 14), I get 70 FPS!

Actually windows itself is an inefficient beast that needs to be re-written from scratch instead of piling more junk on top of a wobbly foundation.

---

### Post by handy on 2011-06-20
Anything that I have used with Wine is always at least as fast as it was on its native Windows. 

For those that need it, a little research can help to clarify & remove many of the misinterpretations of just what Wine is & does.

---

### Post by Perfect Storm on 2011-06-20
Holy Penguin!!! A thread from 2005! Please don't necromancing old threads, thanks.


Thread closed.

---

