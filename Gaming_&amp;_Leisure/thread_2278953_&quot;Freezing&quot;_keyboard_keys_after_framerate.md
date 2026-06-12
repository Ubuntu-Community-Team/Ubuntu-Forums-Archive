---
title: "&quot;Freezing&quot; keyboard keys after framerate drop (native and wine games)"
date: 2015-05-20
forum: Gaming &amp; Leisure
---

### Post by Geaut on 2015-05-20
I am running the latest 64-bit Ubuntu LTS with recommended nvidia driver, although this should not really matter because this problem exists since I switched to Ubuntu one year ago (I regularly update and upgrade). My CPU is an Intel Q6600, I have 2GB DDR2-ram and a GTX 460. Thanks to my rather low RAM my system also often uses parts of my swap partition of 2GB. My Hard-drive is 4 years old and according to the in-build self test in working condition (I also have not experienced any kind of corrupt or lost data).

I mainly play War Thunder (first through wine and now native)  and World of Tanks (wine), but I also have a few hours in Dwarf Fortress (native), Neverwinter Nights (native), Guild Wars (wine), TF2 (native), Left4Dead 2 (native) and Robocraft (native). The following problem I currently only have experienced in World of Tanks and War Thunder.
Directly after joining a battle there often is a significant frame-rate drop (together with loud noises for accessing my hard-drive), but this also can happen in the middle of a battle. If I press any keys on my PS-2 connected keyboard during this frame-rate drop, my keyboard essentially gets unusable. Actions initiated by my keyboard randomly get stuck or ignored (chatting is hard as well), making any kind of movement unpredictable. Disconnecting and reconnecting the keyboard has no effect. My USB mouse still works properly though. This last until I restart the game and only affects the game client and nothing else on my system.

I tried to solve this problem by googling it but it only leads me to unsolved bug reports or very old solutions. Can anyone help me out with my problem? Would it be even solvable with hardware upgrades or is everyone having these troubles?

---

### Post by oldrocker99 on 2015-05-22
You have a pretty old computer (which Ubuntu probably runs very well on). Those games, (a) Robocraft, which says it needs 4GB on the Steam store page, and (b) War Thunder, which appears to only run through wine, is probably (even though its specs state that 1.5GB is the minimum(?!)) running poorly through wine.

Your best solution is another 2GB (or better, 4GB) of RAM. I understand that you may not be in a position to easily get any more, but I suspect strongly that 4GB (or 6GB) would run your games just fine. It will certainly keep your swap partition from being hammered as hard as it sounds like it's doing.

After that, if possible, upgrade your graphics card. The GTX750ti can be procured for ~140 USD, and draws only 60 watts, from the PCI-E slot, which makes it run nice and cool and quiet, and it is nice and fast, faster than the 460, which uses 160 watts and needs a separate power connector.  Here's a comparison between the two:[http://gpuboss.com/gpus/GeForce-GTX-750-Ti-vs-GeForce-GTX-460](http://gpuboss.com/gpus/GeForce-GTX-750-Ti-vs-GeForce-GTX-460). Some might say that the two cards are basically equivalent in performance (which I dispute), but 60 watts versus 160 watts would save you money in the long term!

All said and done here, but your #1 priority for achieving pure Gaming Goodness is to upgrade your RAM.

Good luck!

---

### Post by Geaut on 2015-05-23
> **oldrocker99 said:**
> Those games, (a) Robocraft, which says it needs 4GB on the Steam store page, and (b) War Thunder, which appears to only run through wine, is probably (even though its specs state that 1.5GB is the minimum(?!)) running poorly through wine.

Actually, Robocraft is one of the games that runs really smooth. 
[War Thunder is available for Linux since 6. November 2014]("https://warthunder.com/en/news/2608-war-thunder-is-now-available-on-linux-en") but even running it through wine doesn't change the performance all that much, apart from the problem mentioned in the opening post (for native and wine). The aircraft part has no issues whatsoever actually.

> **oldrocker99 said:**
> Your best solution is another 2GB (or better, 4GB) of RAM. I understand that you may not be in a position to easily get any more, but I suspect strongly that 4GB (or 6GB) would run your games just fine. It will certainly keep your swap partition from being hammered as hard as it sounds like it's doing.  

I definitely see that upgrading my RAM would help out and I appreciate your suggestion, but I was really wondering about this wierd bug I am having. As a sidenote, do you know why games won't register when i press the "left Alt" Key?


Again, thank you for your answer and your suggestions. They don't seem to be bad, but as you already guesssed, I am currently not in the position to upgrade my PC. I am still having trouble to adjust to Ubuntu and especially the keyboard and shortcuts are making me tons of trouble. On windows I never had the problem of my key inputs being unresponsive and it made me very curios, especially after having read some bugreports about it that are several years old.

---

### Post by oldrocker99 on 2015-05-23
I have had no keyboard problems in 7 years of Ubuntu usage, unless the keyboard itself was defective, which has happened, and was fixed by procuring a new keyboard. (Bad news again, I know)

What shortcuts are you having problems with? What do you mean by "games won't register when I press the left ALT key"? Does it simply ignore the keypress? You might want to check the 'keyboard shortcuts" app in Preferences and see if something is awry.

You may be having a hardware problem, rather than an OS problem. Learning any new OS is sometimes a pretty steep learning curve, but Ubuntu Forums is specifically to help anyone with a problem, and the only stupid question is one not asked.

---

