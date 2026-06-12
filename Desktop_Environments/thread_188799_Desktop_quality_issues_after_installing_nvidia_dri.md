---
title: "Desktop quality issues after installing nvidia drivers."
date: 2006-06-04
forum: Desktop Environments
---

### Post by nuvo on 2006-06-04
Hello.
I thought I'd try out XGL under Dapper, so I followed the instructions located on these forums and installed the nvidia driver set.
The problem is that although XGL and everything else works fine, everything has turned incredibly ugly (images look blocky like there's no AA and text looks horrid with some text looking distorted).
The thing is that everything displays perfectly on my smaller LCD screen that I'm using to write this and the problem occurs even before starting Compiz using PHG's thefuture script.

My system specs are:
2.5Ghz Celeron D (ugh!).
256Mb of DDR RAM.
Nvidia GeForce FX 5500 256Mb AGP x8 (only running at x4 and identifies itself as a GeForce 6600, but the box clearly says FX 5500... Though it also has dual monitor support, which it shouldn't, apparently)
27" widescreen LCD HDTV via DVI that runs at 1024x768 max resolution.

The monitor I'm using now is a 15" LCD running at 1024x768.

I'm not interested in having both screens hooked up together as the smaller screen kinda sucks (a bit small and not as bright).
I tried playing with enabling AA, AF and such for the driver, but that made no change (it did make scrolling run slower than a dead turtle though and there were some flickering issues).

Before using the nvidia drivers, the larger screen displayed properly, so I'm guessing it's the driver or XGL that's the problem.
I haven't run into any errors though, so I have nothing to go on really.

Any help would be appreciated.

---

### Post by robert114 on 2006-10-25
Is your problem simulair to mine...
Please take a look at the attachment

---

### Post by Rhubarb on 2006-10-25
> **robert114 said:**
> Is your problem simulair to mine...
Please take a look at the attachment

It doesn't help that the photo there is blurry (just try the read the syncmaster writing on the top left of the monitor).

I can't think why the output would be blurry - It's obviously a driver problem, possibly because your card is improperly detected.

---

### Post by robert114 on 2006-10-25
I'm sorry for the blurry picture, but if you look at the background all what is purple should be black as well as the red above the purple that should be black.

I'll take an other picture when I've aten and i should have a more stable hand.

---

### Post by robert114 on 2006-10-26
I've made an other picture and it is very blurry as well but the collors red, green and purple is the problem it looks like the dark collors arn't rendered properly.

If this topic is about an other problem I'll start a new topic

---

### Post by Rhubarb on 2006-10-31
I see what you mean!
I can't say for sure what's wrong here.

I know with my old Dapper install without the nvidia drivers I would sometimes have all sorts of weird colours around the screen - this was fixed up by running an opengl screensaver.
Now this problem has been completely fixed for me as I'm now running Edgy.

If you've got the bandwidth, try out Edgy (Ubuntu 6.10) and see if that fixes up your problem here.

---

### Post by robert114 on 2006-10-31
Well, this is edgy Kubuntu thanx for your reply.
Do you know a way of describing this problem? so I can start a new thread.

---

### Post by robert114 on 2006-11-02
"Solved" it, I'm now using Ubuntu 32 bit version it solves a lot of problems for me!

---

