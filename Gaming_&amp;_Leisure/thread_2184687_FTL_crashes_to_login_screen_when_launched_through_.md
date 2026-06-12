---
title: "FTL crashes to login screen when launched through steam."
date: 2013-10-30
forum: Gaming &amp; Leisure
---

### Post by nat00 on 2013-10-30
I am currently using ubuntu 13.10, I have steam installed, and I would like to launch FTL (Faster than light). Whenever I try to launch FTL from the steam interface, it launches, the loading screen appears, and then the game crashes and I end up on the login screen. 

I have tried to run FTL with the folowing command : 
> /home/anatole/.local/share/Steam/SteamApps/common/FTL\ Faster\ Than\ Light/data/amd64/lib/libstdc++.so.6 

It didn't work and it gave me this error message : 
> segmentation error (core dumped)

Could anyone tell me how to launch FTL, or at least what is going on?

PS : I used to get the same issue on ubuntu 13.04, so it's not 13.10 related.

---

### Post by oldrocker99 on 2013-10-30
What is your video circuitry and which drivers are you using?

---

### Post by dannyboy79 on 2013-10-30
if you're ending up on the login screen that may mean that not only your game is crashing but your X server is crashing as well.

---

### Post by Blaqksheep on 2013-11-13
This fixed worked for me, as well.  It's worth a try, and easily reversible.

[http://ubuntuforums.org/showthread.php?t=2170323&p=12769183#post12769183](http://ubuntuforums.org/showthread.php?t=2170323&p=12769183#post12769183)

---

### Post by nat00 on 2013-11-15
That did work. Thanks.

---

