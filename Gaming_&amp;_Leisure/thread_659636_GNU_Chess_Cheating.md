---
title: "GNU Chess Cheating?"
date: 2008-01-05
forum: Gaming &amp; Leisure
---

### Post by TimTow on 2008-01-05
This has happened to me two times now.  Put GNU Chess on the hardest setting.  Start winning, and the game makes illegal moves!  Has this happened to other users or am I just not getting it.  here is our move history:  

xboard
hard
force
e2e4
force
e7e5
force
g1f3
force
d7d6
force
d2d4
force
h7h5
force
d4e5
force
h5h4
force
f1b5
force
c8d7
force
b1c3
force
h4h3
force
g2g3
force
f8e7
force
e5d6
force
c7d6
force
e1g1
force
e8f8
force
c1f4
force
d7g4
force
e4e5
force
a7a6
force
e5d6
force
e7f6
force
b5e2
force
d8b6
force
a1b1
force
b6c6
force
c3d5
force
g7g5
force
d5f6
force
g5f4
force
f6g4
force
h8h5
force
d1d4
force
c6c2
force
e2d3
force
b8c6
force
d3c2
force
c6d4
force
f3d4
force
a8e8
force
d4f5
force
h5g5
force
**f5h6**
force
e8e6
force
b1d1
force
g8h6
force
d6d7
force
g5g4
force
d7d8q
force
f8g7
force
f2f3
force
g4g6
force
c2g6
force
f7g6
force
d8d7
force
g7f6
force
f1e1
force
e6e1
force
d1e1
force
f4g3
force
d7e7
force
f6f5
force
e7e5

I highlighted the computer's illegal move in Bold,  I really want to know if there is some special circumstance rule in chess that I just haven't know about all these years...but I'm pretty sure the computer just made an illegal move.  It moved it's pawn diagonal, and took my pawn, but the pawn of mine which it took, was situated directly in front of his pawn, so it moved diagonal to and empty space, and took my pawn anyway...WTF?

---

### Post by FranMichaels on 2008-01-05
Although I'm just a wood pusher when it comes to chess, [En passant]("http://en.wikipedia.org/wiki/En_passant"), is what you are looking for. :KS

---

### Post by BreathEasy on 2008-01-06
Hrm. At first I thought you might have been the victim of the en passant ([http://en.wikipedia.org/wiki/En_passant](http://en.wikipedia.org/wiki/En_passant)) but that can only happen to adjacent pawns, not directly in front. Maybe there's another rule I'm not aware of, or maybe it's a bug that no-one's ever noticed because no-one in their right might would attempt to beat the computer on hard? :)

EDIT: You fell for it too **FranMichaels**. Read his description carefully. :D

---

### Post by FranMichaels on 2008-01-06
> **BreathEasy said:**
> Hrm. At first I thought you might have been the victim of the en passant ([http://en.wikipedia.org/wiki/En_passant](http://en.wikipedia.org/wiki/En_passant)) but that can only happen to adjacent pawns, not directly in front. Maybe there's another rule I'm not aware of, or maybe it's a bug that no-one's ever noticed because no-one in their right might would attempt to beat the computer on hard? :)

EDIT: You fell for it too **FranMichaels**. Read his description carefully. :D

Maybe it is just over my head. To me, his description at the end of his post matches En passant...

"The capturing pawn moves into the empty square over which the moving pawn moved, and the moving pawn is removed from the board"
[http://en.wikipedia.org/wiki/Pawn_(chess)#Capturing](http://en.wikipedia.org/wiki/Pawn_(chess)#Capturing)

EDIT: Also, directly in front, still qualifies as [adjacent]("http://www.m-w.com/dictionary/adjacent").

---

### Post by DoktorSeven on 2008-01-06
Yes, I'm a geek (and very bored, apparently :) ).  I just replayed your entire game, and the move in bold was a noncapturing move by White by a knight.  I didn't see any other move in your move list that resembled a move like you described, or *en passant*, or any sort of illegal move.

---

### Post by SteveNorman on 2008-01-06
en passant it is

everyone thinks Im cheating when I do it also

---

### Post by BreathEasy on 2008-01-06
I have yet to see anyone try an en passant move on a pawn DIRECTLY IN FRONT of another. It's always been to the side. Or at least that's the literature I've seen everywhere.

I'm going to accuse someone of cheating or at the very least, misunderstanding En Passant if they try it in front of me, sorry. :)

---

### Post by ryanVickers on 2008-01-06
yup seems like you people are on the right track... :p

---

### Post by tkmn on 2008-01-06
> **DoktorSeven said:**
> Yes, I'm a geek (and very bored, apparently :) ).  I just replayed your entire game, and the move in bold was a noncapturing move by White by a knight.  I didn't see any other move in your move list that resembled a move like you described, or *en passant*, or any sort of illegal move.

I just replayed the game and can confirm this. :-?

Just a regular move by a knight.. :confused:

---

### Post by TimTow on 2008-01-06
yeah, except that that a knight didn't take the piece, a pawn did.  the illegal move in question involves no knight.  what happened was this:  Two pawns are face to face, at an impasse in the same column, with zero spaces between them.  to be exact, my pawn was in column f space number 6.  his pawn was in column f, space number 5.  he then moved from column f, space 5, to column h, space 6.  this is not en passant.  if you think this is en passant, I believe you are not visualizing the layout of the pieces correctly.

---

### Post by DoktorSeven on 2008-01-06
I did not see a pawn illegally captured this way in the replay of the moves listed above, and I went through it a few times in replay.

Course, as you describe it, it shouldn't happen, since en passant requires moving *behind* a pawn that advances 2 spaces as its initial move.  If you were using a frontend to gnuchess, it could have misinterpreted some move somewhere and showed the wrong thing to you.  That's all I can think of.

---

### Post by incandenza on 2008-01-07
> **TimTow said:**
> yeah, except that that a knight didn't take the piece, a pawn did.  the illegal move in question involves no knight.  what happened was this:  Two pawns are face to face, at an impasse in the same column, with zero spaces between them.  to be exact, my pawn was in column f space number 6.  his pawn was in column f, space number 5.  he then moved from column f, space 5, to column h, space 6.  this is not en passant.  if you think this is en passant, I believe you are not visualizing the layout of the pieces correctly.

I think you are simply confused somehow.  I played through the entire game, and there is no point at which there are pawns on both f5 and f6, nor is there any pawn capture like you describe.

Could you point out the exact move number and what the move was that you think was illegal?  It doesn't seem to be the move you have given in bold, because as many others have pointed out, that was a non-capturing knight move (23.Nfh6).

(Edit: It seems you think there is a pawn on f5 at move 23.  But there's not--it's a knight.  I think you must have gotten the moves mixed up when replaying the game.)

Below is the entire game in standard notation, which may be easier to follow.  No illegal moves.

I can pretty much guarantee GNU Chess will never make an illegal move.  A bug that huge would have been noticed long, long ago.

Also, I suggest loading this into Scid if you haven't tried that program yet--great free chess database.

1.e4 e5 2.Nf3 d6 3.d4 h5 4.dxe5 h4 5.Bb5+ Bd7 6.Nc3 h3 7.g3 Be7 8.exd6 cxd6 9.O-O Kf8 10.Bf4 Bg4 11.e5 a6 12.exd6 Bf6 13.Be2 Qb6 14.Rb1 Qc6 15.Nd5 g5 16.Nxf6 gxf4 17.Nxg4 Rh5 18.Qd4 Qxc2 19.Bd3 Nc6 20.Bxc2 Nxd4 21.Nxd4 Re8 22.Nf5 Rg5 23.Nfh6 Re6 24.Rbd1 Nxh6 25.d7 Rxg4 26.d8=Q+ Kg7 27.f3 Rgg6 28.Bxg6 fxg6 29.Qd7+ Kf6 30.Rfe1 Rxe1+ 31.Rxe1 fxg3 32.Qe7+ Kf5 33.Qe5#

---

