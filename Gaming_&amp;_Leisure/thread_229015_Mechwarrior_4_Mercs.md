---
title: "Mechwarrior 4 Mercs"
date: 2006-08-03
forum: Gaming &amp; Leisure
---

### Post by ironfistchamp on 2006-08-03
has anyone had any success installing this with cedega/wine/cross over?

Also does anyone know what the music to the trailer is called

[http://download.microsoft.com/download/3/6/d/36d74b10-4f1b-4ea0-9ff8-154f7684b5f5/mw4mercs_e3_300k.wmv](http://download.microsoft.com/download/3/6/d/36d74b10-4f1b-4ea0-9ff8-154f7684b5f5/mw4mercs_e3_300k.wmv)

It is driving me nuts :mad:

---

### Post by Limitlesschannels on 2007-04-15
Well, this post may be a tad deflating, but I have been in the same boat for quite some time...

Wine: Failed installation, couldn't get it to work.
Cedega: 1/5 star rating; haven't tried it, but heard it doesn't work
Crossover: no idea; most likely, not.

So, that is rather depressing, but I have been thinking about running VMWare or a virtual box and seeing if I can get it up and running.  I haven't really ran those before, thoguh, so we shall see how successful I will be.

---

### Post by lotacus on 2007-04-16
Wine is legacy, from what I heard what was once wine is now Cedega and Crossover is a fork of wine. Actually I think both Cedega and Crossover are butchering wine and sharing their code with each other. As it stands, Cedega is geared towards game support and Crossover is geared towards applications. Cedega you can get for free quite easily and it's cvs repo is constantly maintained. Which means they don't screw over the GPL and linux users. Cedega, however is quite the opposite, trying to rob you of your money and redifine GPL by claiming all their work is propriatary, which it really is, but in my belief is no way proprietary to THEM, but code stolen/reverse engineered from win32. They will charge you for a so called "subscription" which is just a grey area for charging you for their application, then charge you for support and charge you to "vote" on what game gets more development. Each 'vote' is $5.00. What a shame. Their sources in the CVS are over 5 years old, incomplete, and missing core components (such as the proprietary work) so don't bother trying to compile it yourself.

You will not get the game to work in vmware because vmware doesn't use advanced technology such as 3d support. Until all hardware can use virtualization, you are going to be left with legacy emulation

---

### Post by YokoZar on 2007-04-16
> **lotacus said:**
> Wine is legacy, from what I heard what was once wine is now Cedega and Crossover is a fork of wine. Actually I think both Cedega and Crossover are butchering wine and sharing their code with each other. You heard quite wrong.

Wine is where active development happens.  Versions of Wine are eventually stabilized and incorporated into Crossover, with a few special hacks to make some of Crossover's supported applications work.

Cedega is based off an ancient Wine fork and is developed independently.  New improvements to Wine don't make their way into Cedega, although they do make their way into Crossover.  For this reason, many games run better in Wine than they do Cedega.

---

