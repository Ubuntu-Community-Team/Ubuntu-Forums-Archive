---
title: "Game Access Violation"
date: 2015-02-24
forum: Gaming &amp; Leisure
---

### Post by heroquestelf on 2015-02-24
I recently installed Space Empires IV via Steam (and Wine), but I can't get it to play.

The game loads fine, but then it pulls up the error message: "Access violation at address 00000001. Read of address 00000001."

It appears to have something to do with the fact that the game is trying to run in full screen mode. When the game menu loads, instead of it running truly full screen, the Ubuntu command bar stays in place. Also, the bottom of the menu is cut off. 

Then, once you try and launch the game, it comes up with this tiny 2 inch by 2 inch square in the middle of the screen and you can only see the upper left hand corner of the game. 

I'm puzzled and stumped. I have seen other threads that mention this error, and they have a terminal output. I'm not sure how to get that code or I'd share it as well. Any input on this would be apprecaited, as this is one of my favorite games and I'd love to be able to play it on my Ubuntu machine. 

Also, for the record, I have Wine 1.6 and Winetricks installed.

---

### Post by Rob Sayer on 2015-02-26
Wine has a very good compatability database, and according to it:

[https://appdb.winehq.org/objectManager.php?sClass=version&iId=2540](https://appdb.winehq.org/objectManager.php?sClass=version&iId=2540)

that app is rated Silver.  Generally anything rated less than Gold is unuseable.  Sorry.

---

### Post by mbaucco on 2015-09-22
I was able to bypass this by going into the "Configure Wine" app and checking the "emulate desktop" feature. I set it to 1024 x 768 and it works fine so far. 

-Matt

---

### Post by Bucky Ball on 2015-09-22
*Thread moved to **Gaming & Leisure**.*

If it stays fine could you please see the first link in my signature and mark as solved? Thanks.

---

