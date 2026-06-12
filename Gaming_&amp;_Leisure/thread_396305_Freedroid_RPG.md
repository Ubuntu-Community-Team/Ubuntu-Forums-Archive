---
title: "Freedroid RPG"
date: 2007-03-29
forum: Gaming &amp; Leisure
---

### Post by Flying George on 2007-03-29
I was on the Gamer's Arena, Thank you AI. I was looking for a linux RPG, since Regnum failed for me, and I came across FreedroidRPG. I went to the sf page downloaded it, extracted the file, ran the ./configure file and I got this error: This Game Requires SDL_net library. Since then I've been jumping through hoops going to libsdl.org and trying like hell to sudo aptitude install the package, but no luck. "no packages with SDL_lib in their name" So if anyone knows how to aptitude install it or use the configure.sh file (which I also ./ ran) that comes with the .tar.gz file I downloaded from libsdl.org That would be great.

-Gene

---

### Post by Perfect Storm on 2007-03-29
The libs files you get through synaptic/apt-get/aptitude

The one you are looking for;

```
sudo aptitude install libsdl-net1.2-dev
```
If it can't find it, then it's because you haven't enable universe in your source.list


```
sudo nano /etc/apt/sources.list
```
Read what it says about uncomment (# removing these from the sources).

Then you need to update the list;
```
sudo aptitude update
```
Then try install the sdl net again.


For full/complete sourcelist, check [Source'o'matic](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by Flying George on 2007-03-29
Thanks, that first one worked. I was using an underscore instead of a hyphen, that's probably why. Are there any packages that use underscores, for future reference?

---

### Post by Perfect Storm on 2007-03-29
Sorry second line had a typo, I have corrected it.

---

