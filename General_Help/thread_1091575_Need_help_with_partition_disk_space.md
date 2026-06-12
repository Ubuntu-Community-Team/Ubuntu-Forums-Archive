---
title: "Need help with partition disk space"
date: 2009-03-09
forum: General Help
---

### Post by tahirih on 2009-03-09
before anybody has a chance to give me a hard time, I'm new to Ubuntu and I have little experience with what I'm trying to do. 


I primarily use linux (Intrepid Ibex) but I also have Windows XP on a seperate partition. I'm trying to install and play World of Warcraft on linux. I have wine installed and everything... but when I try to install the WOW, it tells me I need 15 G space. I have 14.8 total. I've tried deleting useless programs on Linux and there still isn't enough room. But I have lots of Gb's available for Windows.

My father did the whole seperate partition thing for me because he is a far more experienced and dedicated Ubuntu user than I am. But he is currently not available for me to discuss this with.

So my main question is: is there a way for me to transfer some space from windows to linux so I can finally install WOW? Any help would be much appreciated because I'm at a loss. Thanks!**[B][B][B]**[/B][/B][/B]

---

### Post by LowSky on 2009-03-09
There is but doing so can break both operating systems for even the most careful of users. 

but there is a work around, If you have a shard space, or if the Windows partion is viewable and large enough for your need, you could always install the WOW files to there, but if your father is the general admin of the PC I would talk it over with him first.

---

### Post by tahirih on 2009-03-09
> **LowSky said:**
> There is but doing so can break both operating systems for even the most careful of users. 

but there is a work around, If you have a shard space, or if the Windows partion is viewable and large enough for your need, you could always install the WOW files to there, but if your father is the general admin of the PC I would talk it over with him first.




the windows partition is viewable, but not through the installer. And my husband is the general admin but i have all the pw's and whatnot as well.

---

### Post by mmyeong on 2009-06-07
[Necro Alert lol]

boot from your ubuntu live c-d ( or an iso burned cd) and run gparted. [sudo gparted]
 
unmount your ubuntu partition, and click resize on the ntfs partition.

after you decrease your ntfs partition, move the unallocated space so it is displayed right next or under your extended ubuntu partition. this can be accomplished by clicking [resize/move] and move your partition bar to the left or the right.

Lastly, once all that is done, resize you ubuntu partition.

---

### Post by merlinus on 2009-06-07
Delete tmp files and defrag your xp partition first.

---

