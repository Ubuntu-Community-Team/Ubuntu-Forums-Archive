---
title: "Brightness Issue"
date: 2009-09-15
forum: Desktop Environments
---

### Post by Veevose on 2009-09-15
I have a wierd problem and i am too dumb to solve it.
My display Brightness is very very dark and i can't make it bright...
I have an nvidia gforce 9500m gs...tried to find some settings there but nothing seems to work for my brightness and its very disturbing because i can bearly see anything. any help please? P.S using ubuntu 8

---

### Post by earthpigg on 2009-09-15
may be silly, but...

laptop?

does it have some combination of buttons that can change brightness?

on my laptop, for example, its [COLOR="Blue"]Fn[/COLOR]+F5.


the F5 button has a small [COLOR="Blue"]blue[/COLOR] picture depicting a bright light-bulb, while F4 has a dark light-bulb.

---

### Post by Veevose on 2009-09-15
> **earthpigg said:**
> may be silly, but...

laptop?

does it have some combination of buttons that can change brightness?

on my laptop, for example, its [COLOR="Blue"]Fn[/COLOR]+F5.


the F5 button has a small [COLOR="Blue"]blue[/COLOR] picture depicting a bright light-bulb, while F4 has a dark light-bulb.


Yes its laptop and yes it has Fn + f5 for up and f6 for down.. and they dont work at all

---

### Post by earthpigg on 2009-09-18
is it noticably brighter on an Ubuntu LiveCD, or when running any other operating system?

if it happens regardless of LiveCD vs install vs completely different operating system, then it is a hardware issue.... LCD displays get dimmer over time.

but, maybe we can fake it:

default brightness:
> xgamma -gamma 1

150% brightness:
> xgamma -gamma 1.5

500% brightness:
> xgamma -gamma 5

i bet you could even add that to system -> administration -> startup applications....

---

