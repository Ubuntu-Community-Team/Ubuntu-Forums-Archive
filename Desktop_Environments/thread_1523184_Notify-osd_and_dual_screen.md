---
title: "Notify-osd and dual screen"
date: 2010-07-03
forum: Desktop Environments
---

### Post by Dark_Raver on 2010-07-03
So i did a install of ubuntu using Wubi. Worked like a charm
got dual screen running too (who can live witouth it these days xD)
problem is
the notifications show up on the second screen, to the right, centered
meaning, its half off screen
is there a way to move it back to its original position on screen 1 while keeping the dual screen setup?
Using ubuntu 10.04 64 bit (thats what wubi said at least :p)

EDIT: i seem to have located 1 problem with the dual screen, it looks like it doesn't have the same resolution.
Just downloaded a package and saved it to the desktop, but it appeared half off screen too, so il give some info regarding the settings
screen 1, laptop -> 1680 * 1050
screen 2, external screen -> 1440*900
can't run them both on the same rest
both run on max res, if i put laptop on 1440*900 i get distorted image (kinda :p) and gives me headaches (non native res)

---

### Post by artemyv on 2010-07-03
this blog post [http://leolik.blogspot.com/2009/12/notify-osd.html](http://leolik.blogspot.com/2009/12/notify-osd.html) (in russian) contains a link to ppa with patched version of osd-notify which could be configured using simple cofig file

bubble-vertical-gap = 5px
bubble-horizontal-gap = 5px

parameters specify the distance from the right and top border of the screen.

I suppose - modifying these parameters you'll be able to move the bubble to desired location...

In some  post I have read something about configuring them using GUI - but cannot remember where it was and how complete it was

---

