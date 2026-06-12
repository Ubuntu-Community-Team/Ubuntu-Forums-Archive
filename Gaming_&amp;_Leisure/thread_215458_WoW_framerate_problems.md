---
title: "WoW framerate problems"
date: 2006-07-14
forum: Gaming &amp; Leisure
---

### Post by Orunitia on 2006-07-14
Okay I installed WoW a couple days ago, it installed fine and I can play it. My problem is that I can only get 15-20 fps, while on windows I got 30-60, depending on the area. I **really** don't want to go back to windows, not even dual boot as it feels like a waste of space to me. Any suggestions besides going back to windows, and turning down the settings? I have an nvidia card, I'm running it with nvidia-settings --load-config-only, and running it in opengl. I've tried it without all that too, same deal.

---

### Post by Perfect Storm on 2006-07-14
Well, you could try with Cedega or CedegaCVS, Patrick wrote a installation script for it somewhere.

---

### Post by Orunitia on 2006-07-14
Unfrotunately cvscedega didn't work for me, so I just reinstalled XP as a dual boot. :( I refuse to pay for cedega when I have XP sitting here.

---

### Post by vem0m on 2006-07-14
ummmmm cedega is cheap then XP's Problems lol pay for one month $5 then stop paying tell it to not update nor log in and BOOM u got free FULL cedega :D

---

### Post by Orunitia on 2006-07-14
> **vem0m said:**
> ummmmm cedega is cheap then XP's Problems lol pay for one month $5 then stop paying tell it to not update nor log in and BOOM u got free FULL cedega :D

Not sure what you said but... okay.  It's not the price. I don't want to pay for cedega when I'm not even sure it will run WoW better for me than wine did. (And with how well wine is SUPPOSED to run WoW, I doubt it will run it any better.)

---

### Post by vem0m on 2006-07-14
it did for me lots better and its worth a try dude as XP takes up space and causes more problems then its worth to play a game on lol up to u, but as i said pay for one month of cedega u d/l it and use it cancell payment don't uninstall just tell it to not login anymore to a cedega account and disable updating and u can use the version u were using then on out for free.

---

### Post by joemo75 on 2006-07-14
Did the original poster verify that she had the proper graphics drivers installed?

---

### Post by Polygon on 2006-07-14
i also find that cedega is a waste of money, i mean im not going to pay for the game, pay for my computer, pay for internet, pay any game subscription fees and THEN pay for some program to run the game in linux. Ill use windows or wine thank you very much.

---

### Post by vem0m on 2006-07-14
apperntly u guys do not understand the term pay for it then stop and u have a full program to run those games last time i will repeat this as it has been said enough times now

---

### Post by DoktorSeven on 2006-07-14
> **vem0m said:**
> apperntly u guys do not understand the term pay for it then stop and u have a full program to run those games last time i will repeat this as it has been said enough times now

I assume you mean purchasing the 3-month Cedega minimum subscription then cancelling, so that you have the latest version of Cedega after the 3 months are over forever.

Unfortunately, the problem with this, especially with World of Warcraft, is that in the past WoW patches have broken compatibility with Cedega and the only way to fix it is to get a new version.  Imagine being stuck with an old version of Cedega when a new version of WoW is released, keeps your old version from working, Transgaming releases a fix, and you're unable to get it... it's happened to me. :(

---

### Post by vem0m on 2006-07-14
well i had np with the 5.2 engine heh i still use 5.2.1 and it works great :)

---

### Post by Orunitia on 2006-07-15
> **joemo75 said:**
> Did the original poster verify that she had the proper graphics drivers installed?



...She? ](*,) :neutral: 

And yes, I have the proper drivers installed. I had everything setup correctly unfortunately. Oh well. :( I have other games I'll keep windows around for too anyways, no big deal. Thanks anyways everyone.

> **vem0m said:**
> apperntly u guys do not understand the term pay for it then stop and u have a full program to run those games last time i will repeat this as it has been said enough times now

Yes, I understand, you don't have to repeat it. That's just more money I have if I keep windows around and not waste it on cedega when I'm not positive it will fix my problems.

---

### Post by stimpack on 2006-07-15
Sadly Orunitia I think your best option is to use Windows for WoW. Frame-rates are alot better. I tend to mess about under Cedega, but for raids I have to reboot into Windows, as a laggy priest is not very helpful.

I have been trying to find a solution to this problem, as some people claim that it runs better under Wine than Windows. I did find one guy that claimed the problem was Ubuntu's bastardized kernal and that other distros do not have this problem.

---

### Post by vem0m on 2006-07-15
that is totally untrue Ubuntu has a good version of the kernal no differant then any of the others that work good it varies from one computer to the next one setup to the next and one system configuration to the next ubuntu is the fastest distro i have used.

---

### Post by Perfect Storm on 2006-07-16
I'm with vem0m on this one. When I was playing Wow (not playing it anymore). I used Cedega on Ubuntu and it worked fine. Yes, also in raid.

---

### Post by gaillard on 2006-07-16
everyone keeps saying it runs "fine" or yes it "works" or such... but if its 5 fps lower then its not. :(   

I havn't found anything that runs faster graphics wise in ubuntu with benchmarks... please people do a benchmark and not just say it feeeeels faster ...

---

### Post by eqisow on 2006-07-16
> I havn't found anything that runs faster graphics wise in ubuntu with benchmarks... please people do a benchmark and not just say it feeeeels faster ...

Pretty much anything native runs faster than it does on Windows. Games such as WoW and WCIII are also faster for me, since they're done in OpenGL. Loading times, in particular, are much shorter. This isn't just speculation either.

Now, back to the OP's issue. Are you running WoW in OpenGL mode? Another issue might be RAM. Since the Wine loads the Windows API into RAM when it runs, you need more memory to play WoW in Wine than you do in Windows. If you're not running at least 1 GB, this may be the issue. If you have an ATI video card, this may be an issue as well. Their Linux drivers are pretty shoddy and there may be a performance difference due to that.

---

### Post by Orunitia on 2006-07-16
> **eqisow said:**
> Pretty much anything native runs faster than it does on Windows. Games such as WoW and WCIII are also faster for me, since they're done in OpenGL. Loading times, in particular, are much shorter. This isn't just speculation either.

Now, back to the OP's issue. Are you running WoW in OpenGL mode? Another issue might be RAM. Since the Wine loads the Windows API into RAM when it runs, you need more memory to play WoW in Wine than you do in Windows. If you're not running at least 1 GB, this may be the issue. If you have an ATI video card, this may be an issue as well. Their Linux drivers are pretty shoddy and there may be a performance difference due to that.


Running in OpenGL, I have a gig of ram, and I have an nvidia card.

---

### Post by vem0m on 2006-07-16
ATi is not an issues i run with an Ati with 1.3 GB system ram just fine thu cedega Ati rumor about it being bad and not working as well need to stop its all lies if u set ur drivers up u will be fine, Linux ATi drivers are great i have used them with 2 differant ATi chips and NEVER had any issues with framerates

---

### Post by eqisow on 2006-07-16
The actual performance of the ATI drivers may be fine (I was simply speculating) but the drivers are still shitty. Support for new ATI cards is generally months behind Windows support. Linux ATI drivers don't even support Crossfire yet. The configuration utility for Linux ATI drivers is also greatly lacking.

NVidia Linux drivers don't really keep up with their Windows counterparts either, but NVidia puts much more effort into their development than ATI does. Bottom line.

---

### Post by vem0m on 2006-07-16
nvidia puts alot of time into marketing and trying to be seen thier performance lacks behind ATi and they burn in wrong and burn out quick causing lack of performance that well they already lacked but to each thier own that is proven facts of the GPU chip world(i am a computer repair technician) :)

---

### Post by eqisow on 2006-07-16
I wasnt refering to either companies GPU's, only the effort they put into serving the Linux community. Here, Nvidia wins hands down.

Even so, I find the two companies GPU's tend to stay quite close to each other performance wise. Besides, which company can outperform the other with their bleeding edge chips is of no concern to me. I'm more concerned with cost/performance ratios, which also happens to fluctuate between the two companies.

Of course, the reason my last card was an Nvidia is simply because they continued to sell decent AGP cards longer than ATI did.

Now let's get this thread back on topic...

---

### Post by stimpack on 2006-07-16
> **eqisow said:**
>  Loading times, in particular, are much shorter. This isn't just speculation either.

Oh yes, loading is indeed much faster, both instance loading and the loading of player models.

Its just this wierd FPS problem, just 10fps less, but when Ive only got 20 under windows, its a lot to lose :). nvidia here too.

---

### Post by nalthien on 2006-07-16
Not sure what it does, but I change dthe following in my Config.wtf:

```
SET fullAlpha "1"
```

to

```
SET fullAlpha "0"
```

and my framerate GREATLY improved.

---

### Post by vem0m on 2006-07-16
could have just changed tha ingame its a GFX setting

---

