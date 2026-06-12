---
title: "Hoping SecondLife doesn't suck this time."
date: 2007-08-15
forum: Gaming &amp; Leisure
---

### Post by CheshireMac on 2007-08-15
Hey folks. I'm currently downloading SecondLife for Linux in Alpha mode. It was really glitchy for the two hours I played with it on Dapper, but I'm hoping that on Feisty, after giving development some time, it might work now. Has anyone had any experience with Second Life on Ubuntu? I could really use some tips if there's any to be had.

---

### Post by Cochise on 2007-08-15
used it on windows and found it very buggy - that was quite a while ago, installed it the other night on ubuntu and it seems 10x better. [www.getdeb.net](www.getdeb.net) is where i got it from, they packages loads of new versions of apps for ubuntu.

---

### Post by CheshireMac on 2007-08-15
I'm running it (the newest version) as we speak, and it's just as glitchy as the last time. Same computer, running on Feisty now, but the frames are super slow, and I can't seem to edit my appearance (The option is not selectable) . . . I don't know if this is because it's only Alpha, or if my computer just can't support the Viewer properly, but it's lagging immensely. I thought maybe running Wine would do something for the Windows version (Isn't the Windows Viewer supposed to be quite good?) I don't have an M$ platform to speak of, only Feisty. I'm hoping I don't have to give up on this. Wish me luck. ~LOL~ By the way, anyone know off hand if Wine takes up a lot of memory?

---

### Post by CheshireMac on 2007-08-18
Okay. I've now figured out what the problem is, but I'm not sure how to fix it.
I switched to Xfce today to see if that would stop the crashes, but to no avail. It only makes it run a little smoother. 
Someone in the SL world told me that it was an issue with my video card and so I took a look here.
```
mac@mac1:~$ sudo lsmod | grep intel_agp
intel_agp              24348  1 
agpgart                34096  2 drm,intel_agp
```
Problem is, I'm not sure what to do with this info. She said rename it and something or other (this was just before another crash.) Any help would be appreciated. Thanks.

---

### Post by cmat on 2007-08-18
It's the glitchiest, buggiest piece of crap in history. Buggy player movement and collision detection.  Some areas take minutes to render with my 3MB/s connection. Not to mention the various horrors and fetishes people make very apparent.

---

### Post by CheshireMac on 2007-08-19
> **cmat said:**
> It's the glitchiest, buggiest piece of crap in history. Buggy player movement and collision detection.  Some areas take minutes to render with my 3MB/s connection. Not to mention the various horrors and fetishes people make very apparent.
Aside from indivi_dual weirdness, _is there any way to overcome the crashes?

---

### Post by cmat on 2007-08-19
Is it an integrated video card? Intel is really tricky in terms of gaming. I know someone that was going ape over buying a very impressive laptop and not being able to play BF2 on it. I was going nuts trying to find the solution then I asked what his hardware was, Intel graphics. After that it was a closed case. Intel cards and gaming are a lost cause.

---

### Post by Hendrixski on 2007-08-22
> **Cochise said:**
> used it on windows and found it very buggy - that was quite a while ago, installed it the other night on ubuntu and it seems 10x better. [www.getdeb.net](www.getdeb.net) is where i got it from, they packages loads of new versions of apps for ubuntu.

lol, I just posted a question about that on several of the other SecondLife threads.  Whether or not [http://www.getdeb.net/release.php?id=1240](http://www.getdeb.net/release.php?id=1240) worked well.

I think I'm going to give it a try tonight and see what all the hype is about, I'm curious to see the things that certain universities are putting up on there, and why businesses are looking into holding virtual meetings on there.

---

### Post by Hendrixski on 2007-08-25
Ok, wow, I tried the debs from getdeb.net and it's easier to install than the windows version.  Even works better on linux on the same computer.  :-)

As for SL itself... it's fun to explore parts of the island, and the Ubuntu Pyramid is a pretty nice gathering spot.  Basically, SL is like the next generation of IRC... because it's 3D.  It needs a lot of work.  I don't think I'll be using it much, but I'll check in once in a while to see if it's getting better, because it's a very exciting technology.

---

