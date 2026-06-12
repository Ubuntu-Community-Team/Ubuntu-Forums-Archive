---
title: "Childrens Chess"
date: 2010-05-16
forum: Gaming &amp; Leisure
---

### Post by kneewax on 2010-05-16
Hi folks, 

I've just started playing Chess with my 6yr old. He is obsessed already and I wondered if anyone new a Chess program that has a setting that is easy for smaller kids. The easiest settings on glchess is too advanced for him, so I am looking for something with a simple engine that will help him develop his skills without getting hammered every time!

Anyone got tips on a good chess program for kids?

---

### Post by DangerOnTheRanger on 2010-05-16
Maybe eboard would be just the thing; it allows you to play chess against a chess engine(Sjeng, Crafty, or GNU Chess), and you can change the move depth(how far into the "future" the engine searches) very easily. I would recommend a move depth of 2, maybe 4.

Plus, you can play online, on FICS, so that's something to keep in mind, as well.

Here are instructions for setting eboard so your 6yr old can play comfortably:

Install eboard and Sjeng by typing:
```

sudo apt-get install eboard sjeng

```Then, open up eboard by typing **eboard** at the terminal, or by menu(**Applications > Games > eboard**).

Open up the Sjeng's settings by going to **Peer > Play against Engine > Sjeng.. **.

Set Depth Limit to 2, to start with.

Uncheck Think on opponent's time.

Select Time Control... .

Set the Type combo box to "Fischer clock(ICS-like)"

Set Starting Time to 05:30:00 .

Set Increment to 60:00 .

Press OK.

Press OK again.

Now the game will start, and you can avoid all that trouble by selecting the only bookmark in **Peer > ICS Bookmarks **.

That should do it!

---

### Post by kneewax on 2010-05-17
thanks I'll try that and see how he gets on!

---

### Post by DangerOnTheRanger on 2010-05-17
Let me know if you run into any problems!

---

### Post by new_tolinux on 2010-05-17
Try Windows 7 (maybe also Vista) chess.

I made it compete with GNU Chess -> first pc black against human, other pc white against human.
Until Windows Chess was set to level 4, it was beaten every time by GNU Chess.

---

### Post by new_tolinux on 2010-05-17
double post

---

