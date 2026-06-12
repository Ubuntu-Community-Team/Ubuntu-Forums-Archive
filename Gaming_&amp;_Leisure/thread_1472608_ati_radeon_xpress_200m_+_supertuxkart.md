---
title: "ati radeon xpress 200m + supertuxkart?"
date: 2010-05-04
forum: Gaming &amp; Leisure
---

### Post by Alex Chad on 2010-05-04
Hi,

I'm kind of new to ubuntu but I am really enjoying the alternative to my xp partition, long story short I'm doing battle with my graphics card. I'm on a old Advent laptop (7105) with ati radeon xpress 200m graphics card, and having read around I gather that there's many issues with a card this old, but I just wanted to ask before I replaced it. I'm trying to play some simple games like supertuxkart and get compiz opengl working but with no success. Any help would be appreciated, and if there's no help and my cards at the end of the line where would you suggest looking for a replacement? Which brand and/or model has the best support in ubuntu?I'm using karmic right now.

Thanks loads.

---

### Post by prions on 2010-05-04
I have that same card, xorg support for it died off in the upgrade from 8.10 to 9.04. I hardly play games on my Ubuntu partition, but the open source drivers work pretty well. You can probably get most simple games to work. 

I'd suggest replacing the card, and although I don't like Nvidia at all, it has better Ubuntu stability and support than Ati.

---

### Post by Alex Chad on 2010-05-04
Thank you for the reply, its a shame they discontinued it. Suppose this means my xp partition lives another day.

Cheers again.

---

### Post by prions on 2010-05-04
I still have my windows partition for games. Its not worth the effort to get games to slightly work on Ubuntu when my xp partition is a simple boot away. I'm not dissing Ubuntu, but games aren't what it excels at.

---

### Post by pme 72 on 2010-07-04
SuperTuxKart worked well for me with Karmic 64 bit using an ATI x1550. I did a fresh install of Lucid 32 and on some of the more demanding courses the x1550 struggled. At times some of the track would disappear. I installed an ATI HD4550 and the problem cleared up, that was using the open source drivers.  

My integrated card is an ATI Radeon Express 200G (RS480). SuperTux Kart would not run with the open source drivers in Hardy but when I enabled the proprietary driver it worked. In Jaunty it worked with the open source drivers. I was concerned about the cpu draw so I upgraded to the x1550 and later bought the HD4550 but found the x1550 worked better with the open source driver until Lucid.

Compiz worked for me with Karmic and the 200G. I only changed back to the x1550 because I could not get suspend to work with the 200G and thought STK might not perform well.

You could try Hardy 8.04 which should be supported for almost another year-as long as Karmic. My 200G was supported by the proprietary driver. Compiz is enabled by default in Hardy but my 200 card was blacklisted. To get Hardy to boot I started in safemode the first time and enable the proprietary driver. After that it was smooth sailing.

---

