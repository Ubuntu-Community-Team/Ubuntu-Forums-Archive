---
title: "Chess960 - FRC"
date: 2007-09-04
forum: Gaming &amp; Leisure
---

### Post by tmcmurph on 2007-09-04
Is there any Chess960 or Fischer Random Chess games available for Ubuntu?

I have downloaded eboard and fruit but can't get eboard to use any engine other than what it came with.

I did have a chess960 game running under nexenta (gnusolaris) but since I switched to ubuntu in May I can't find the files to recompile.

It was a glalrung + special xboard + polygot configuration.

Thanks

---

### Post by tmcmurph on 2007-09-14
Well I solved the problem and have a great new setup. I didn't have to compile anything which is good because I still can't find some of the files I need.

If you download Jose Chess Database and the Fruit 2.2.1 engine you can then play Chess960 (aka FRC). Don't let the engine name throw you off. It is amazingly strong. Even with rook odds it is hard to beat.

The install was simply to untar the Jose files then the fruit files. Move the fruit directory into jose/engines and add the engine from the game gui.

Too easy.

---

### Post by kwtm2 on 2008-07-30
May I please ask: what do you do after you get the Fruit engine running?  In particular, how do you activate the Chess960 feature?  I don't see any "Generate Chess960 starting position" menu item.  I'm presuming that it's more than just using the "set up the board the way you want" feature (which would be present in any chess engine, not just Fruit).  How do you get it to generate a random Chess960 starting position?

Also, I saw a number of databases in the Jose Chess Database.  I downloaded "performance.bin".  Is there any particular database to download?  Is there one for Chess960 specifically?  Since the idea of Chess960 is to use tactics, not a pre-compiled opening book, I presume that the database itself is not that important to the computer game.  Is that right?

> **tmcmurph said:**
> Well I solved the problem and have a great new setup. I didn't have to compile anything which is good because I still can't find some of the files I need.

If you download Jose Chess Database and the Fruit 2.2.1 engine you can then play Chess960 (aka FRC). Don't let the engine name throw you off. It is amazingly strong. Even with rook odds it is hard to beat.

The install was simply to untar the Jose files then the fruit files. Move the fruit directory into jose/engines and add the engine from the game gui.

Too easy.

---

### Post by tmcmurph on 2008-12-06
On the menu under "File" "New FRC"

FRC is Fishcher Random Chess where Chess 960 came from.

---

### Post by tmcmurph on 2010-10-03
Install Xboard and polyglot from the Unbuntu software center then put your Chess 960 engine in a folder and start like this

xboard -fcp "~/chess/fruit_221_linux/fruit_221" -fUCI

In this case a folder in my home dir named chess with the fruit chess960 engine in it. Once started you can run it by "File, New Variant, FRC, OK".

If you don't want to start from the command line System, Preferences, Main Menu can take you there to put that line in properties.

---

### Post by kwtm2 on 2011-03-11
> **tmcmurph said:**
> On the menu under "File" "New FRC"

FRC is Fishcher Random Chess where Chess 960 came from.

Glad you posted to this after a 2-year gap.  I still need help.

I am using xboard after installing polyglot (there is no Jose client in Ubuntu repositories), by typing at the command line 

xboard -fcp ~/bin/jose/engines/fruit -fUCI

There is no actual menu entry "File > New FRC".

There is "File > New Variant... > FRC".  When I select, an error pops up: "Fischerandom not supported by Fruit 2.1".

I am able to make do with the "File > New Shuffle Game..." entry; I guess I'll reject any starting position that doesn't meet Chess960 requirements, but this is not quite Chess960.  (For example, I think castling rules are different between Shuffle Chess and Chess960.)

How did you get Fruit to support the Chess960 variant?

---

### Post by kwtm2 on 2011-03-11
> **kwtm2 said:**
> an error pops up: "Fischerandom not supported by Fruit 2.1".
I found the answer.  Fruit 2.2, but not Fruit 2.1, supports Chess960.  Fruit 2.2 is not currently in the 10.04 repositories, and I had to download it directly from its home page.  There is no compilation; the executable binary is ready to go, to be used with xboard as specified above.

---

### Post by bicyclerepairman85 on 2013-01-16
Sorry to drag this thread up again!

I'm interested in playing FRC chess. I've downloaded XBoard and Fruit 2.2. I'm using the version of polygot included in Fruit 2.2 (couldn't find it in the Software Center). 

I start XBoard like this: 


xboard -fd /home/user/chess/fruit_22 -fcp ./polyglot

It opens up, with "Fruit 22" in the title bar, so I'm sure it's working. However, all variants under File->New Variant are greyed out. Any ideas what I'm doing wrong?

Thanks!

---

