---
title: "Quarry is Missing the GTP Engines"
date: 2007-01-28
forum: Gaming &amp; Leisure
---

### Post by NotPhil on 2007-01-28
I installed Quarry because it said it had a nice port of GRhino, an Othello/Reversi game, in it. But all it seems to have are the boards for Go and Reversi; there are no AI opponents. I looked around the Ubuntu repositories for the GRhino GTP plug-in, but couldn't find it. GRhino's home page doesn't even mention it.

Does anyone know where to find, or how to activate, the AIs for Quarry? Or, better yet, does anyone know where to find a package of GRhino, or Sirius, that will run under Ubuntu?

---

### Post by tecteun on 2007-11-12
better late then never :P maybe someone wants to know:

install gnugo and add the following command as gtp engine 
gnugo --mode gtp --level 5
(or an other level of play)
for othello/reversi you can use grhino and the command "gtp-rhino"

---

### Post by Chymera on 2007-11-16
10x for the reply, as a matter of fact someone DID want to know, do you have any idea how i can get gnugo? it's not in the repos...

---

### Post by jr_tyrrell on 2007-11-20
I can help there Goban isn't so much a game as an engine for doing Go so you don't find it in the add/remove programs go to the synaptic package manager (System -> Administration -> Synaptic Package Manager). Search for GnuGo and it will appear in the list click on it to install and then apply the changes. Then just follow tecteun's post.

---

### Post by BobSongs on 2008-05-11
> **tecteun said:**
> better late then never :P maybe someone wants to know:

install gnugo and add the following command as gtp engine 
gnugo --mode gtp --level 5
(or an other level of play)
for othello/reversi you can use grhino and the command "gtp-rhino"

Excellent. I managed to get **Go** working with> gnugo --mode gtp --quietbut had difficulty trying to add the **rhino** engine. Your code worked perfectly.

Just a point about playing Reversi in Quarry: when selecting the Computer as your opponent, you have to select the Reversi engine (GTP Grhino) as it will not select it by default. Beyond that... both **Go** and **Reversi** work flawlessly.

Thanks.

---

### Post by jtpoole99 on 2008-09-27
Are there any other game engines besides the two mentioned above?

---

