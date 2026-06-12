---
title: "Solitaire Aisleriot"
date: 2007-12-31
forum: Gaming &amp; Leisure
---

### Post by joebanana on 2007-12-31
How can I set Solitaire that will deal one card at a time with unlimited redeal. I can only find an option for one card deal, and I can turn two decks or tree card deal, and unlimited redeal.

---

### Post by acoustibop on 2007-12-31
FWIW the configuration file appears to be at ~/.gconf/apps/aisleriot, joebanana.

---

### Post by compiledkernel on 2007-12-31
sudo apt-get install pysol 

PySol is a bit more versatile in my opinion as opposed to aislerot.

---

### Post by disturbedite on 2007-12-31
i'm really digging patience in kde4.  contrary to the name, (maybe it should be changed), it supports about a dozen types of solitaire.  it looks absolutely amazing.  i wish it had more games like pysol.  (maybe it will get more in the future).

---

### Post by joebanana on 2008-01-06
Is there any option in pysol to adjust the card size to the screen resolution. I haven't found this option. In my case the cards look so tiny. Thought this is what I was looking for.

---

### Post by fromgi on 2008-01-31
If you want unlimited redial, then you'll have to change the program: /usr/share/gnome-games/aisleriot/games/klondike.scm.  You'll find: (define max-redeal 2).  Change this number to whatever redeal you want; perhaps 99 instead of 2.  You'll also notice this game has a comment "Fix Me".  I'm surprised Ubuntu would include anything that knowingly needs to be fixed into their production version.  After looking at this program, you'll also notice the game with either hold onto an ace or king, in addition to other short-comings . Can you imagine someone shuffling a deck of cards and holding onto a few?

---

### Post by txmxmatt on 2011-01-07
Does anyone know the shortcut to automatically move the cards up to the appropriate stacks once all cards are on the board? I use the keyboard shortcut ctrl + enter to move cards one at a time, and every once in a while I will somehow hit a keystroke combo that moves them all, but I can't seem to figure out what I'm hitting.

---

