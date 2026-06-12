---
title: "MAME and MESS"
date: 2007-11-20
forum: Gaming &amp; Leisure
---

### Post by inversekinetix on 2007-11-20
Would anyone be willing to give me a hand installing MAME and MESS latest versions with gui frontends.  Ive been trying for a few weeks and cant figuire it out


any help appreciated

---

### Post by disturbedite on 2007-11-20
sdlmame
kxmame cvs (compile the tar that has sdlmame support) -- frontend  (don't install the package in the ubuntu repos, its outdated & doesn't support sdlmame)

---

### Post by inversekinetix on 2007-11-21
> **disturbedite said:**
> sdlmame
kxmame cvs (compile the tar that has sdlmame support) -- frontend  (don't install the package in the ubuntu repos, its outdated & doesn't support sdlmame)

Ive been using linux for about a month.

how do i get these files that I need,  I tried to compile sdlmame1.20 but i think it messed up.

i tried kxmame from synaptic and it crashes if you resize the screen.


can you provide links for the files I need please?  also front ends for both mame and mess.

---

### Post by baqai on 2007-11-22
For MAME i use Ksmame you can find it under Add / Remove it works for me just fine

---

### Post by disturbedite on 2007-11-22
no no no, no one is listening to what i said.

_***don't install the kxmame package in the ubuntu repos, its outdated & doesn't support sdlmame***_

second you can get sdlmame packages here:
[http://wallyweek.altervista.org/index.php](http://wallyweek.altervista.org/index.php)
so there is no reason to compile sdlmame.

but you do have to compile kxmame, and since no can seem to find it, i'll list it for everyone:
[http://sourceforge.net/project/showfiles.php?group_id=145736&package_id=174814&release_id=514402](http://sourceforge.net/project/showfiles.php?group_id=145736&package_id=174814&release_id=514402)
and here is a tip:  if you can't get to finish compiling, disable the joystick with:  ./configure --disable-joystick

---

### Post by inversekinetix on 2007-11-22
thanks, Ill try it.  what about mess?  which version of that works?

---

### Post by wingnux on 2007-11-23
Were you able to compile kxmame? configure and ./configure does nothing on the tar directory =/

---

### Post by disturbedite on 2007-11-23
then you're obviously doing it from the wrong directory.

---

### Post by cmonkey on 2007-11-23
Go into the trunk directory, and type:
make -f Makefile.cvs

That will make a configure and Makefile for you.  Then you can:
./configure  --disable-joystick && make && make install.

---

### Post by keyboardslave on 2008-01-03
> **disturbedite said:**
> then you're obviously doing it from the wrong directory.

dude, you realy need to learn to explain proply. i cant even follow your directions and iv been using linux for a while. Its great your trying to help but theres no point if you dont give DETAILED directions.
Kind Regards,

---

