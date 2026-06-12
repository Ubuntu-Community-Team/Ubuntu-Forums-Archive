---
title: "Need help installing Daimonin"
date: 2010-10-31
forum: Gaming &amp; Leisure
---

### Post by ThePhysician on 2010-10-31
Having a really rough time installing the game.

I downloaded the source from [http://www.daimonin.org/download](http://www.daimonin.org/download) and then I installed the dependencies for the game.

Now when I cd into ~/client/make/linux and try to ./configure it puts out:

```
bash: ./configure: No such file or directory
```

Which prevents me from moving on to the next step.

And I am currently in the proper directory, according to the guides I've seen. I have a file called configure.in in this folder.

---

### Post by WienerWuerstel on 2010-10-31
```
sh ./bootstrap && sh ./configure && make install
```This should work.

---

### Post by ThePhysician on 2010-11-01
That got it to work. Thanks!

Sadly, after installing the game the UI almost made me vomit all over my keyboard. Time to look for another game. =P

---

