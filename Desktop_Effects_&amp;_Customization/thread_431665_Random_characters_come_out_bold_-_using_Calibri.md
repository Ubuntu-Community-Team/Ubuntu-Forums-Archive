---
title: "Random characters come out bold - using Calibri"
date: 2007-05-03
forum: Desktop Effects &amp; Customization
---

### Post by almightybunghole on 2007-05-03
Hi folks,

I have a really strange issue which I can't even work out how to search for help with, hence this post. Basically what happens is, when using certain apps (i just noticed it in Gaim) some combinations of characters are displayed as bold when the rest of the text is rendered as usual. I'm using Calibri as my desktop font, not sure if it's related to that or not.

Combinations of characters that seem to be affected are: ti - ff - fi - tf (with this combo, only the "t" is bold) 

There are others. Does anyone have any clue what this might be? I've never seen anything like it before. FYI, I'm running Feisty beta (going to upgrade soon) and running Beryl on an HP nx9420 (ATI x1600 gfx).

Cheers!

George

---

### Post by Nytron on 2007-12-07
bump

---

### Post by sysop073 on 2008-04-11
I have this problem too. I think the issue is that Calibri combines certain characters together into [ligatures]("http://en.wikipedia.org/wiki/Typographical_ligature"), and they don't show up right on Linux for reason. I'm not sure how to fix it, but that might help your search

---

### Post by SEMW on 2008-04-11
I've had this problem too.  One fix is to run "sudo dpkg-reconfigure fontconfig-config" and select "Autohinter" (the Ubuntu default is 'native').  This hugely antialiases everything (similar to Mac OS font rendering) so it makes all the your fonts fuzzy round the edges, but fixes the calibri/cambria/Segoe problem.  

Personally, I've just stopped using Calibri as a desktop font; since I dislike the fuzzy edges that using the autohinter gives.

---

