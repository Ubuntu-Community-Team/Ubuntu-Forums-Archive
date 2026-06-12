---
title: "ioquake3 intrepid"
date: 2008-11-01
forum: Gaming &amp; Leisure
---

### Post by Benjamin_Vedder on 2008-11-01
Hi

I have just installed intrepid (a fresh install), but i simply cant run ioquake3 anymore. In hardy and all previous releases it worked just fine.

i get:
```
ioquake3.i386: error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory
```
and i have no idea why. I have the latest nvidia drivers installed (177.80), and other games run well, even openarena which uses the ioquake3 engine as far as i know. I have also tried
```
sudo ln -s /usr/lib/libopenal.so /usr/lib/libopenal.so.0
```
without success. I remember i had an error like this with an fresh install of hardy too, but i dont remember how i solved it, so now after googling for some hours i decided to post here to see if anyone can help me.

I also noticed, in hardy i had libopenal0a installed, but it does not seem to be present in the intrepid repos, but another package called libopenal1 is.

So, any ideas?

Thanks in advice

---

### Post by gladstone on 2008-11-09
Same issue here, though this solved it:```
sudo ln -s /usr/lib/libopenal.so.1 /usr/lib/libopenal.so.0
```

---

