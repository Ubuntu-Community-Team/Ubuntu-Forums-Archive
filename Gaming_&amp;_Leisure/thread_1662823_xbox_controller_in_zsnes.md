---
title: "xbox controller in zsnes"
date: 2011-01-08
forum: Gaming &amp; Leisure
---

### Post by garyhibdon on 2011-01-08
tried to use the controller in zsnes to play a couple of games, configured the button inputs, etc, etc, etc. its acting like the controller should be working properly but upon entering the actual game, none of the controls actually and it typically crashes zsnes. any ideas?

btw, wired xbox controller on ubuntu 10.10

---

### Post by garyhibdon on 2011-01-08
noone can help me????

---

### Post by garyhibdon on 2011-01-09
still could use a little direction . .

---

### Post by garyhibdon on 2011-01-09
ok. i give up.

---

### Post by garyhibdon on 2011-01-10
through further investigation, ubuntu version 1.51 of zsnes appears to not support the xbox controllers. ill update this in the future should i find a way to make it work. email me if you happen to have already found a way please

---

### Post by thatguruguy on 2011-01-10
Have you considered using a different emulator? I use snes9x, and it seems to have no problems with my (generic) xbox controllers.

---

### Post by garyhibdon on 2011-01-11
ok sorry. upon further investigation i found that this will fix the problem 100%.


```
sudo apt-get install qt4-qmake
```
after that, zsnes will understand it 100%, so configure the buttons and enjoy!!!

---

### Post by glave on 2011-03-01
> **garyhibdon said:**
> ok sorry. upon further investigation i found that this will fix the problem 100%.


```
sudo apt-get install qt4-qmake
```
after that, zsnes will understand it 100%, so configure the buttons and enjoy!!!

Care to elaborate on that? I'm working on mine now, and indeed, the controller isn't working. I installed qt4-qmake (not that I thought this alone would fix things) and nothing changed.

---

