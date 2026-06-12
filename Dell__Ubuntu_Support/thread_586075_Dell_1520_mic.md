---
title: "Dell 1520 mic"
date: 2007-10-21
forum: Dell  Ubuntu Support
---

### Post by jonghwa on 2007-10-21
what's up?

I installed Ubuntu Gutsy 7.10 on Dell Inspiron 1520.

Everything's fine now, but I have an issue since 7.04 Feisty.


The plugin microphone works, but the volume is [COLOR="Red"]too low[/COLOR]. Koreans say it sounds like ants crawling. :)

I multi-boot with Vista. I don't have this problem on Vista.

what's the problem?



I installed a driver as follows:

sudo apt-get install linux-backports-modules-generic

---

### Post by linux23dragon on 2007-10-22
> **jonghwa said:**
> what's up?

I installed Ubuntu Gutsy 7.10 on Dell Inspiron 1520.

Everything's fine now, but I have an issue since 7.04 Feisty.


The plugin microphone works, but the volume is [COLOR="Red"]too low[/COLOR]. Koreans say it sounds like ants crawling. :)

I multi-boot with Vista. I don't have this problem on Vista.

what's the problem?



I installed a driver as follows:

sudo apt-get install linux-backports-modules-generic

Did you use your Volume Control Preferences (Found in your Volume control) to enable Mic Boost (+20db) ?

---

### Post by jonghwa on 2007-10-23
it works fine now, I think I'm so stupid.


However, I had to set "Digital Input Source" "Analog Inputs" instead of "Digital Mic 1". How different is Analog Inputs from Digital Mic 1? still stupid  :(


Digital Mic 1 also works but very low sound recording...


Thanks.

---

### Post by ericstoesser on 2008-03-07
how did you get it working? im having problems getting the mic to load up...

---

