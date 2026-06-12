---
title: "Installing Glest Advanced Engine"
date: 2009-04-17
forum: Gaming &amp; Leisure
---

### Post by LiamWilson on 2009-04-17
Hey all;

I have just installed Glest 3.2.1 via a .deb, and I now need to install the Glest Advanced Engine for the ability to save my game. 
Does anybody know how to install it, and where I can get a Linux/Ubuntu version?

Any help would be greatly appreciated;

LiamWilson

---

### Post by Vadi on 2009-04-17
I think that should have came with the .deb...

Can you try this version? [http://www.getdeb.net/search.php?keywords=glest](http://www.getdeb.net/search.php?keywords=glest)

---

### Post by LiamWilson on 2009-04-18
Yeah, that's the one I downloaded, but it doesn't include the advanced engine as far as I'm aware.

---

### Post by disturbedite on 2009-04-18
> **LiamWilson said:**
> Hey all;

I have just installed Glest 3.2.1 via a .deb, and I now need to install the Glest Advanced Engine for the ability to save my game. 
Does anybody know how to install it, and where I can get a Linux/Ubuntu version?

Any help would be greatly appreciated;

LiamWilson

instructions are right on the home page:

[http://glest.codemonger.org/home_page.php](http://glest.codemonger.org/home_page.php)

---

### Post by LiamWilson on 2009-04-19
Yeah, but it says I need to download "glestadv-data", and that isn't even featured on the page!

Great, yeah, I've downloaded the files, where do I extract them to?

---

### Post by disturbedite on 2009-04-19
> **LiamWilson said:**
> Yeah, but it says I need to download "glestadv-data", and that isn't even featured on the page!

Great, yeah, I've downloaded the files, where do I extract them to?

it is implied that the reader knows what he/she is doing. but it does say right there in the instructions:

"The glestadv-data package will overwrite a few Glest files (menu.xml, english.lng, etc.)" so you need to stick it where Glest's data folder is. in opensuse, mine is located in /usr/share/games/glest/data.

---

### Post by LiamWilson on 2009-04-19
Thanks! Because I had installed it with a .deb, I wasn't sure where the files had been installed to. Thanks, disturbedite!

---

### Post by disturbedite on 2009-04-19
> **LiamWilson said:**
> Thanks! Because I had installed it with a .deb, I wasn't sure where the files had been installed to. Thanks, disturbedite!

no problem.

i hadn't actually installed GAE myself yet. i have this problem when starting glestadv:

Exception: Can't open propertyMap file: glestadv.ini

game won't start. suggestions?

---

### Post by LiamWilson on 2009-04-19
Hmm, this GAE really is more trouble than it's worth. 

Try searching for it in the Glest file, if it's there, it could be in the onf the bz's.

Update://

It can be found in the 'glestadv-0.2.11-generic-x86_64-pc-linux-gnu.tbz2'. Just extract it to your /usr/share/games/glest directory

---

### Post by hailstone on 2010-12-18
Hi, I'm one of the programmers of Glest Advanced Engine. GAE is now standalone and [the latest release]("http://glest.org/glest_board/index.php?topic=6283") comes with deb package and win32 installer. If you have any problems post on [the forums]("http://glest.org/glest_board/index.php?board=15.0") and someone will be happy to help out.

---

