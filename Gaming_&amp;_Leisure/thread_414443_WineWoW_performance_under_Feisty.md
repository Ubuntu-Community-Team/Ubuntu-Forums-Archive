---
title: "Wine/WoW performance under Feisty"
date: 2007-04-19
forum: Gaming &amp; Leisure
---

### Post by NeonNazgul on 2007-04-19
Greetings all.

I've had World of Warcraft running under Wine perfectly for a while now with 6.10.  Today I (of course) upgraded to Feisty and reinstalled everything clean.  WoW is working perfectly again, but I *think* I've noticed a drop in performance.  I notice it most when turning -- frame rate "stutters" more than it used to.

I don't have Beryl/Compiz installed, and I'm using the Restricted Drivers Manager to load the nVidia driver.  I'm wondering if that's the culprit?

It's not a major hit, and the game is quite playable.  Just wondering if anyone else has noticed this?

Cheers

EDIT:

Never mind.  Forgot to do the registry tweak found here:

[http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)

All is well again.  I am so SMRT :)

---

### Post by puccha on 2007-04-23
> **NeonNazgul said:**
> 
It's not a major hit, and the game is quite playable.  Just wondering if anyone else has noticed this?


EXACT same problem here, performance is reasenable but turning gives a major fps dip. For me it was unplayable.

> 
Never mind.  Forgot to do the registry tweak found here:
[http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)


TY for posting this, worked for me. I had the tweak but I made a typo somewhere... d'oh! WoW now even works well on top of compiz for me. that was never the case for edgy, neat! /kiss Neon

---
Edit, turned out this didnt help me all that much, some but not enough however setting my terrain distance to a minimum helped and I playing like never before =)

> **dspari1 said:**
> I got the best performance by turning down tarrain distance to a minimum **AND** turning off vertical sync. Because of this, I'm now running the game at 38fps outside on my P4 2.4ghz, 1gb of ram, and Geforce 6600GT 128mb. 

---

### Post by slowhands36 on 2007-04-25
iam glad you guys can get it to work cause for me it sucks bad   load wow in wine screen  is really slow  

stops for 10 to 12 seconds then moves a bit again  cant even get to part to log in


iam using a ATI x600 video card  is this the problem or something else

---

### Post by NeonNazgul on 2007-04-25
> **slowhands36 said:**
> 
iam using a ATI x600 video card  is this the problem or something else

I have tried and tried to get my x800 to run WoW acceptably under Wine, and I eventually gave up.  Swapped out my x800 for my wife's nVidia 7600.  Was a bit of a downgrade performance-wise, but at least things *just work* now.

ATI has horrible drivers for Linux.  Apparently they're trying to get their act together but I wouldn't hold my breath.  Sorry to say, but the ATI card is most likely the problem.

For Linux gaming, nVidia, love 'em or hate 'em, is the only real choice.

---

### Post by justin whitaker on 2007-04-25
> **slowhands36 said:**
> iam glad you guys can get it to work cause for me it sucks bad   load wow in wine screen  is really slow  

stops for 10 to 12 seconds then moves a bit again  cant even get to part to log in


iam using a ATI x600 video card  is this the problem or something else

The ATI drivers are not so good. 

I'm using Crossover, NVIDIA 6600, getting frame rates from 35-75fps depending on what is going on ingame, and latency < 100.

Way better than XP on the same machine.

---

### Post by Ferrat on 2007-04-25
Im using a x800 and my FPS and preformance has if anything become better since I updated to feisty?

---

### Post by NeonNazgul on 2007-04-25
> **Ferrat said:**
> Im using a x800 and my FPS and preformance has if anything become better since I updated to feisty?

That's good to hear.  I might just give it another shot and see if I can get my beefier card back ;)

Any troubles/tips about making ATI work?

---

