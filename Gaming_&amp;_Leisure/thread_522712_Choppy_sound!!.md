---
title: "Choppy sound!!"
date: 2007-08-10
forum: Gaming &amp; Leisure
---

### Post by logreeval on 2007-08-10
I get really choppy sound when Im trying to play frozen-bubble, torcs to name a few...

Do you guys know how to make it not choppy?, its so annoying i cant even play them. :mad:

Thanks

---

### Post by logreeval on 2007-08-11
bump...

It seems to just happen on the more 3d games...

---

### Post by Nevon on 2007-08-11
I know what you mean, I get the same in Savage. Have no idea why it happens though.

---

### Post by logreeval on 2007-08-11
I get it on most of my good 3d games... :-S

I can only play solitaire :P

---

### Post by Nevon on 2007-08-11
I haven't really gotten any other good 3d games to work on Linux yet, besides Savage, so I can't say for sure, but it seems we're having the exact same problem.

---

### Post by logreeval on 2007-08-12
and it is annoying... ;-P

---

### Post by Contrast on 2007-08-12
Same problem here. It happens to me on most of my fairly CPU-intensive games, and even with ZSNES. :-\

---

### Post by logreeval on 2007-08-12
There has got to be a way to not have that happen, I mean the game runs fine, just the sound isn't quality.

I hope someone knows what to do...

---

### Post by logreeval on 2007-08-12
I really can't find anything...i don't know if it has to do with the type of sound the games use?

---

### Post by logreeval on 2007-08-14
I found the answer...Close topic...

---

### Post by chriswyatt on 2007-08-15
Share the solution, I have the same problem.

---

### Post by logreeval on 2007-08-15
Ok :)

You have to make a file in your home directory thing....like Home/NAME

The file is called .asoundrc

Put this code into the file:

> pcm.!default {
type hw
card 0
}

ctl.!default {
type hw
card 0
}

When done save it, the file should disappear, then restart.

I hope that helps.

---

