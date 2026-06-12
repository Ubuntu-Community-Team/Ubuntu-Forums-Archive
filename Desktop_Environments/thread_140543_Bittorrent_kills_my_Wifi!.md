---
title: "Bittorrent kills my Wifi!"
date: 2006-03-06
forum: Desktop Environments
---

### Post by MahRain on 2006-03-06
When I'm using the internet, working in Openoffice, whatever, and have a Bittorrent client running for some time, I will loose my Wifi connection. I have checked this by running KWifiManager and I see my status *suddenly* change from "Excellent, Top or Ultimate" to "Out of Range" and it reports 'No networks found'.

I have tried this using Bittornado (latest release) and Azureus 2.4.0.0 and both result in the same issue.

The Wifi is unencrypted and connected to a Netgear WPN824 (running as B+G) router. The chipset on the card is a Prism II (802.11b). 

I have tried bittorrent on port '24708' and on 6881-6899. Same difference.

(When NOT using any bittorrent application my connection stays stable for hours, if not days.)

---

### Post by lupine_nickt on 2006-03-06
I get the exact same issue using aMule and an rt2500 usb device (D-link dwl-g122 rev. b1) - module rt2570.ko

All I can think of that it might be, is the 802.11 stack being unable to handle so many connections (both upstream & down), and bombing out - but that's just a guess.

I'm waiting for Dapper to be released, in the hopes that it'll have a 2.6.13 or higher kernel (I can't be ar$ed to roll my own ;) ). If it does, then an alternative 802.11 stack becomes available (for me, at least; don't know about your driver), which might resolve the problem, if my guess is right. 

xF,

...Nick

---

### Post by FlakJacket on 2006-03-06
I also get this exact same problem.  Really wish I knew how to fix it. Also happens sometimes if I download a large file from firefox.  I usually just close all internet apps like gaim and firefox and let Azureus run by itself and it works.

Flak

---

### Post by Jason_25 on 2006-03-06
I've seen this happen too.  I figured bittorrent was crashing the router I was connected to.  Maybe not though.

---

### Post by MahRain on 2006-03-09
[QUOTE=lupine_nickt]I get the exact same issue using aMule and an rt2500 usb device (D-link dwl-g122 rev. b1) - module rt2570.ko

All I can think of that it might be, is the 802.11 stack being unable to handle so many connections (both upstream & down), and bombing out - but that's just a guess.

I'm waiting for Dapper to be released, in the hopes that it'll have a 2.6.13 or higher kernel (I can't be ar$ed to roll my own ;) ). If it does, then an alternative 802.11 stack becomes available (for me, at least; don't know about your driver), which might resolve the problem, if my guess is right. 

xF,

...Nick[/QUOTE]
Just now I upgraded to kernel 2.6.15-ck6 and the problem persists!

---

### Post by GeneralZod on 2006-03-09
[QUOTE=lupine_nickt]I get the exact same issue using aMule and an rt2500 usb device (D-link dwl-g122 rev. b1) - module rt2570.ko
...Nick[/QUOTE]

I think it's a driver issue, rather than a kernel one:

[http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=237](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=237)

---

### Post by MahRain on 2006-03-09
[QUOTE=GeneralZod]I think it's a driver issue, rather than a kernel one:

[http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=237](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=237)[/QUOTE]
Could be, however, I have a "Intersil Corporation Prism 2.5 Wavelan chipset (rev. 01)" PCI-based card.

So not an USB issue and probabily not related to the RT2500 driver?

---

### Post by GeneralZod on 2006-03-09
[QUOTE=MahRain]Could be, however, I have a "Intersil Corporation Prism 2.5 Wavelan chipset (rev. 01)" PCI-based card.

So not an USB issue and probabily not related to the RT2500 driver?[/QUOTE]

That was a reply to **lupine_nickt** :)

---

### Post by FlakJacket on 2006-03-09
MahRain I think I have close to exactly the same card that you have.  I really hope to find a solution.

Flak

---

### Post by mistamcgoo on 2006-03-10
I don't know if this is anyhow related, but i did a firmware update on my linksys wrt54g wireless router yesterday, and in the version.info(1/17/2006) i saw this 
> 
- Resolves issues with instability when using Bittorent


hope this can help anyone

---

### Post by Sokar on 2006-09-15
I have the same problem, when i put azureus, or amule.. my wifi gets down and reconnects after a while.

I konw that it isn't a problem of my router, cause i've installed win xp in the same pc and these p2p run great with the same config i use in linux...

If i don't put any p2p, mi wifi connection is solid, if i put it, it's only a matter of time.. it will fail at 5 or 25 minutes, but will get down...

I'm using ubuntu with kernel 2.6.15-26, all updates, and the wifi is intel 3945abg...

---

