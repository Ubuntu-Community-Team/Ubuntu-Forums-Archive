---
title: "Firefox page loading problem"
date: 2009-03-31
forum: General Help
---

### Post by steviefordi on 2009-03-31
For the most part my internet connection works well. Every now and again however I visit a page or site (well my wife does) that takes an eternity to load (about 5-10 minutes).

Two examples I have are [www.netmums.com](www.netmums.com) and [www.next.co.uk](www.next.co.uk). These sites load fine on my desktop which uses Hardy with Firefox, however on my laptop using Intrepid with Firefox I have this problem.

There must be something about these sites that either conflicts with my setup, or exposes a bug. 

I am using ndiswrapper to drive the wireless card, could this be the problem? Or could it be I haven't installed Java or Adobe Flash Player? I'm really lost for things to try.

My wife keeps nagging me to put Vista back on the laptop as it 'worked fine when we bought it'. I really don't want to have to do that so If anyone has got any idea what it might be I'd be grateful for your advice.


Cheers
Steve.

---

### Post by philinux on 2009-03-31
Try running firefox in safe mode. Addons are known to cause problems, running in safe mode with bypass them.

Open a terminal, Applications>accesories>terminal

Then just use 

```
firefox -safe-mode
```

as the command and press enter. Try your problem sites and see what happens.

---

### Post by steviefordi on 2009-04-02
Thanks for the advice philinux. I tried that and it didn't make any difference, so I tried a different browser and that didn't work either.

I then wired my laptop directly to the modem and found it worked fine so I thought the problem must be with ndiswrapper or the windows driver ndiswrapper uses.

I managed to find a native linux module (ath5k) for my Atheros wireless card and got that working by installing linux-backport-modules-generic. Madwifi, the driver that ships with Ubuntu for Atheros cards, doesn't work with my device. If I'd have known it was that easy to get the more up-to-date ath5k driver installed in place of madwifi I'd have never bothered with ndiswrapper in the first place!

After all that my problem sites load in seconds. I just don't know if I should file a bug report to the ndiswrapper guys?

---

