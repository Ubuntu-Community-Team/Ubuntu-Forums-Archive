---
title: "Free Tennis 0.1"
date: 2005-10-31
forum: Gaming &amp; Leisure
---

### Post by KingBahamut on 2005-10-31
Free Tennis is a tennis simulation developed by a former tennis player. Its main feature is realism. For gameplay, this means you have total control over the shot parabola. For graphics, it means players have realistic gestures. For AI, it means real tactics.

**License:** free

**Additional System Requirements:** OCaml Compiler to Build 

[IMG]http://happypenguin.org/images/freetennis.png[/IMG]

Links
[http://freetennis.sourceforge.net/](http://freetennis.sourceforge.net/)

---

### Post by ndtoan13 on 2005-12-01
I found this in readme file (or something like that)
Install the packages ocaml, lablgtk2, lablgl, camlimages, ocamlsdl
(the actual package names could be different).

Can anyone tell me extrackly the name of all that packages? And how to get them if they are not in synaptic?

(I can not get from csv, it said that csv command not found)
Thank you.

---

### Post by dolny on 2005-12-01
its cvs not 'csv' ;)

---

### Post by jrib on 2005-12-01
looks great, I am going to try to compile it now

[e]it compiled fine and I played a few sets.  The controls take a while to get used to.  One thing that makes the game difficult for me at least is that I will often find myself moving my player to the edge of the court by dragging my mouse in that direction but then it will suddenly change to aiming mode and I have to change directions to get the ball to stay on the court.

I'm going to keep it installed though and see if I can get the hang of it.

Would anyone like to try the human vs. human mode? :D

---

### Post by ndtoan13 on 2005-12-01
[QUOTE=dolny]its cvs not 'csv' ;)[/QUOTE]
Sorry, It's my typing mistake. I have copy the command from guide cvs..., but it still the same.

Also, I can not Install all the packages lablgtk2, lablgl, camlimages, ocamlsdl. Just ocaml pack, can you tell me their name?

I have download v0.4.8 and unzip, then type make command, but it said ocaml compiler not found!!

What can I do?

@Jason : I'm newbie to tennis, so I need an newbie too to play human vs human.
After I have tennis, I want to fight vs you (you have some days (while I try to install) to practice if need! :D )

---

### Post by ndtoan13 on 2005-12-04
Hello,

After try my best, I still can not install tennis!!! 
> $ make
ocamlopt   -I +camlimages  -I +lablGL -I +lablgtk2    -I +sdl -o freetennis  bigarray.cmxa sdl.cmxa lablgtk.cmxa lablgl.cmxa  ci_core.cmxa  sdlmixer.cmxa sdlttf.cmxa unix.cmxa freetennis.ml
File "freetennis.ml", line 43, characters 0-13:
Unbound module Sdlevent
make: *** [all] Error 2
That is all I get. Please tell me how to install the game?

---

### Post by linbetwin on 2005-12-04
Does this game look as good as the screenshot? Are the players' movements easy to controll?

---

### Post by seguso on 2005-12-04
[QUOTE=ndtoan13]Hello,

After try my best, I still can not install tennis!!! 

That is all I get. Please tell me how to install the game?[/QUOTE]

You need to install ocamlsdl.
If you have other problems, please ask in the forum. Read INSTALL.txt first. :-)

---

### Post by seguso on 2005-12-04
[QUOTE=linbetwin]Does this game look as good as the screenshot? Are the players' movements easy to controll?[/QUOTE]

"Yes" to both questions. Isn't it easier to try the game? ;-)

---

### Post by seguso on 2005-12-04
[QUOTE=ndtoan13]Sorry, It's my typing mistake. I have copy the command from guide cvs..., but it still the same.

Also, I can not Install all the packages lablgtk2, lablgl, camlimages, ocamlsdl. Just ocaml pack, can you tell me their name?

I have download v0.4.8 and unzip, then type make command, but it said ocaml compiler not found!!

What can I do?

@Jason : I'm newbie to tennis, so I need an newbie too to play human vs human.
After I have tennis, I want to fight vs you (you have some days (while I try to install) to practice if need! :D )[/QUOTE]

The exact package names for ubuntu are mentioned in the INSTALL.txt file. You have to enable the universe though.

---

### Post by harisanwer on 2009-03-08
How could free tennis be compiled under windows

---

