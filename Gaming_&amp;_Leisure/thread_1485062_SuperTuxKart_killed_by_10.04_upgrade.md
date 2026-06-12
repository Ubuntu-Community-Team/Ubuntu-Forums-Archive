---
title: "SuperTuxKart killed by 10.04 upgrade"
date: 2010-05-16
forum: Gaming &amp; Leisure
---

### Post by Grench on 2010-05-16
I have two Compaq Evo Pentium 4 desktops (stock on-board video) that are set up for my 8 year old twins to use and play games on.  I upgraded them from 8.04 to 10.04 recently and have been able to get most things working on them.

However, SuperTuxKart dies spectacularly at the screen where they are supposed to select their Kart/driver.  The Kart pictured rotates a couple of notches and then the screen blanks, goes to vertical white bars, blanks, the monitor looses video signal, blanks, does the white bar thing again, etc...  The only way out is to hit Alt-Ctrl-Del a few times/hold them and it will cleanly re-start Ubuntu.

I have tried windowed/non windowed and every available resolution on the video configuration menus.

The game was working fine under 8.04.

Any suggestions are appreciated.

Thank you.

---

### Post by fooman on 2010-05-16
> **Grench said:**
> I have two Compaq Evo Pentium 4 desktops (stock on-board video) 
....

sounds like a graphics driver issue....do you know what video card is in there (nvidia, ati, intel, etc) ??

if you are not sure,  open a terminal and run the following:

```
lspci
```

post the results back here.

---

### Post by Grench on 2010-05-17
I will try to run that later tonight.  

Both of the kid's computers are stock-on-board business graphics though.  They were able to run SuperTuxKart on 8.04 -barely-.  I will not be too shocked if they can't keep up.

When I had them open last I noted that they have an AGP4x slot in them.  Putting a cheap 3d card in there would probably help matters.  I did some searching around, but I haven't been able to find a suggestion for an AGP card that is readily available, under $35 each (I have to buy 2) and simply works with Ubuntu.

Do we have a hardware compatibility matrix anywhere?

Thank you.

---

### Post by Grench on 2010-05-17
> **Grench said:**
> I will try to run that later tonight.  

Both of the kid's computers are stock-on-board business graphics though.  They were able to run SuperTuxKart on 8.04 -barely-.  I will not be too shocked if they can't keep up.

When I had them open last I noted that they have an AGP4x slot in them.  Putting a cheap 3d card in there would probably help matters.  I did some searching around, but I haven't been able to find a suggestion for an AGP card that is readily available, under $35 each (I have to buy 2) and simply works with Ubuntu.

Do we have a hardware compatibility matrix anywhere?

Thank you.

I found another constraint.  These machines only have 175W PSUs.  So, the card has to be low draw.

---

### Post by Grench on 2010-05-17
Searching has revealed an Nvidia 6200 based card that might fit the bill.  Price, availability and power envelope work.

The only bits I could find on Linux compatibility were from 2006+/- and likely no longer apply.

I'm betting that it will work find - but may as well check.

Does anyone have a Nvidia 6200 based card in their system?  Will it simply work?  Require patience and command line work?  Not work at all?

Thank you.

---

### Post by hikaricore on 2010-05-17
I have a 6200 on an old system running karmic.
It was enough for xbmc and some emulators, I can't imagine tuxcart being too harsh for it.

Results may vary however.

---

