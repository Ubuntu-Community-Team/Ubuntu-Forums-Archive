---
title: "Porting Games Over"
date: 2008-05-04
forum: Gaming &amp; Leisure
---

### Post by k33bz on 2008-05-04
Ok, I have a question on what all would you need, software as well as hardware, to port over a game. As well as how many _man hours_ it would take to port over a very large game.  And is there any legal things one would have to go through as well?

---

### Post by Grishka on 2008-05-04
> **k33bz said:**
> Ok, I have a question on what all would you need, software as well as hardware, to port over a game. As well as how many _man hours_ it would take to port over a very large game.  And is there any legal things one would have to go through as well?

that depends on the game. some stuff can be ported easily, but some have to be rewritten almost from scratch. for example, some commercial software uses proprietary libraries. legal restrictions depend on the software as well. most commercial games cannot be legally ported, without publisher's consent.

---

### Post by hessiess on 2008-05-04
games cannot be easely ported without source code, this rules out most games.

---

### Post by k33bz on 2008-05-04
ok, this may be an illegal question, if it is, please inform me, and delete this reply.

Is there a way to extract, like reverse engineer a game, for its source code? if there is how do you do this?

---

### Post by unbuntued on 2008-05-04
> **k33bz said:**
> ok, this may be an illegal question, if it is, please inform me, and delete this reply.

Is there a way to extract, like reverse engineer a game, for its source code? if there is how do you do this?
There are reverse-engineering tools available out there. But nothing will get you from assembly to source code in one-click. You need to to go through the generated code line by line and rewrite it.
One such tool is the Interactive Disassembler: [http://www.hex-rays.com/idapro/](http://www.hex-rays.com/idapro/)
This was how OpenTTD was started.

---

### Post by k33bz on 2008-05-04
would that tool work for a windows game that is extremely large, and that uses high graphix and direct x

---

### Post by cb951303 on 2008-05-05
the question depends highly on the used libraries. if its a directx game you can forget about porting it. because if you do so it's called rewriting the game not porting it :)

also for a large game, if you don't have the source code, don't bother. Porting a game without it's sourcecode is between hundreds_of_year_long and impossible

I didn't know about openttd but it's understandable since chris sawyer used to code his games in assembly. I suspect reverse-engineered assembly code of ttd meant a lot more to the openttd guys than any game written using a structural or oo programming language would :)

---

### Post by eragon100 on 2008-05-05
If he could somehow get the source code (or reverse-engineer it), couldn't he compile against wine-lib? Wouldn't that make it work good under wine?

That is how wordperfect (I know that's not a game :)) was "ported" to linux, when there still was a linux version, it even shipped that way with corel linux when that still existed :guitar:

---

### Post by cb951303 on 2008-05-05
> **eragon100 said:**
> If he could somehow get the source code (or reverse-engineer it), couldn't he compile against wine-lib? Wouldn't that make it work good under wine?

That is how wordperfect (I know that's not a game :)) was "ported" to linux, when there still was a linux version, it even shipped that way with corel linux when that still existed :guitar:


as I said before it highly depends on the library used. wine is no where near complete, especially for directx which most windows games use. 

also it seems that there is a misunderstanding about reverse engineering. it's a good method to port device drivers or to figure out some proprietary file format but to port a game with reverse engineering is out of question. A very simple application, maybe, but a big game, no...

I also think that openttd team only reverse engineered the file formats that ttd used and they rewrite the engine from scratch to use those data files. I don't see why someone would want to reverse engineer an entire game to get hold of its sourcecode in place of rewriting it.

cheers

---

