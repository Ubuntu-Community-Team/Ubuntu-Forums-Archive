---
title: "GNU Chess Eats up processor"
date: 2007-04-13
forum: Gaming &amp; Leisure
---

### Post by buntu_hugenewbie11 on 2007-04-13
I play against the GNU chess engine using Py chess and the engine uses up 100% of my CPU even after the game ends. Anyone know why this may happen?
I use feisty (64) and KDE.
Also does anyone know why a draw after repeated moves does not seem to occur?

---

### Post by hikaricore on 2007-04-13
As far as cpu usage is concerned, this is the AI using your processor as it's "brain" to play against you.  Though it should stop after a match ends or closing the game.  Check your processes to make sure it's not still running even though you think it closed.

---

### Post by DoubleQuadword on 2007-04-13
> **hikaricore said:**
> this is the AI using your processor as it's "brain" to play against you.

That's not the point, and, in fact, that doesn't justify that amount of processor usage either. It's not supposed - anyhow - for a chess game to use that amount of processing just to find which move is the best to take. Actually, it does not matter (at all) how he set up the game, it cannot end up taking - anytime - more than 1% of his CPU. That's definitely a bug.

Regards.

---

### Post by red_Marvin on 2007-04-13
I'm not really agreeing, since a chess AI works (AFAIK) by checking all possible moves and countermoves a number of steps into the future, (and possibly checks with a database of known plays) and then determine the route to take to get the best possible outcome.

Say that it looks three moves/countermove sets into the future and that each time there's eight possible moves, that means it has to build a tree with 8+8^2+8^3+8^4+8^5+8^6 = 299592 entries and then determinine the best outcome, that seems like it could be quite intense IMO...

---

### Post by kevinlyfellow on 2007-04-13
Does it eat up processor when it is using an opening book?

Edit:  I just tested mine, and my processor didn't ramp up.  I also didn't give it much of a chalenge ;-)
Edit Again:  Harder modes seem to use lots of processor.  Does gnuchess have books, it took a long time for it to make its first move?

---

### Post by red_Marvin on 2007-04-13
I don't think so, however I'm not sure if it's using an opening book...

I think that the difficulty setting determines how many steps in the future it examines, and since the tree grows exponentially, the differences between process loads would be quite big.

---

### Post by DoubleQuadword on 2007-04-13
> **red_Marvin said:**
> I think that the difficulty setting determines how many steps in the future it examines, and since the tree grows exponentially, the differences between process loads would be quite big.

Quite logic isn't it?

What I tried to explain is the fact that one algorithm cannot use the whole processor capacity every time it executes. Think of it: "GNU chess smothers your processor.", something is not going well, is it?

Nevertheless, please note that I'm not questioning the algorithm efficiency, but certainly I think it needs a revision, at least, for the advanced difficulty modes.

Regards.

---

### Post by red_Marvin on 2007-04-13
If I understood you correctly you mean that it *shouldn't* be coded so that it eats up all cpu power and leaves nothing to other application? I agree to that, but personally I've found linux resource managment efficient enough to not choke other applications too much when more than one cpu consuming app is running. However it might be a bad idea to play chess on the hard setting with a heavy matlab simulation in the background;) ...


EDIT::
I see now that I misread the original post; of course the cpu usage should drop when the program ends, sorry for my ignorance...

---

### Post by DoubleQuadword on 2007-04-13
> **red_Marvin said:**
> it shouldn't be coded so that it eats up all cpu power and leaves nothing to other application?

Exactly, that's what I meant.

> **red_Marvin said:**
> personally I've found Linux resource management efficient

Me too, Linux resource management is highly efficient. Linux is indeed overwhelming.

> **red_Marvin said:**
> sorry for my ignorance...

Why apologize? I don't think you're an ignorant whatsoever. :)

Regards.

---

