---
title: "Making Hybrid ATI/Intel Graphics Work Nicely"
date: 2013-11-08
forum: Desktop Environments
---

### Post by pokepal101 on 2013-11-08
(Sorry if this is in the wrong section, it's not *exactly* DE related)

Alright, I have a **HP Pavilion DV7-6108TX** laptop running **Ubuntu 12.04**. It has a **dual ATI/Intel** graphics setup. [FONT=courier new]lspci[/FONT] shows:
Intel card: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09), shows up as &#8216;Intel® Sandybridge Mobile&#8217; under Settings.
ATI card: Advanced Micro Devices, Inc. [AMD/ATI] Whistler [Radeon HD 6730M/6770M/7690M XT] (rev ff)

Usually, I use the Intel card (to save battery and keep the temperature down), but sometimes I want to do something graphics-intensive, like play DotA 2 or something.
Currently, the only thing I can do is run [FONT=courier new]aticonfig --px-dgpu[/FONT], log out, log back in, play the game, run [FONT=courier new]aticonfig --px-igpu[/FONT], log out again and log back in again.
Obviously if I do this, I lose all the applications I had open before.

My question is, is there some nicer way of doing this, so that I could at least keep my existing running applications? (For example, making X switch graphics cards without restarting itself, or running two separate X sessions side-by-side, one for each graphics card).

EDIT: Forgot to mention, I have AMD Catalyst Control Center installed.

---

### Post by pokepal101 on 2013-11-26
**I have discovered a &#8216;solution&#8217;!**

If your X session is running on the integrated graphics card, and you run [FONT=courier new]aticonfig --px-dgpu[/FONT] and then switch user to a *different* user account, the new user account will use the discrete graphics card! So, what I've done is create two user accounts, a standard and a gaming account. I run my regular apps on the standard account with the integrated graphics card, then when I want to play a game, I run [FONT=courier new]aticonfig --px-dgpu[/FONT], switch user and log into to my gaming account. And all my apps stay open! Yay!

This may not be a suitable solution for everyone, but it works for what I gotta do!

---

