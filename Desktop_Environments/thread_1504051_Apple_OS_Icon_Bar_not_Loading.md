---
title: "Apple OS Icon Bar not Loading"
date: 2010-06-07
forum: Desktop Environments
---

### Post by tomnewton on 2010-06-07
Hey there, I'm not sure where to post this, but the title of this sub-forum seemed relevant, so I'm gonna post here. Admins, please move to where it should be if it shouldn't be here please. Thanks.

So I was looking around the interweb for some gnome themes for my Lucid Lynx, and I have come across quite a few where the screens show an Apple OS style icon bar at the bottom of the screen. This is one thing I love about Apple (you don't know how much it hurts me to say I love anything about Apple. Die-hard Apple/Steve Jobs hater over here ):P), so I installed a few of these themes.

However much to my dismay, after installing these themes, the Apple-esque icon bar failed to materialise!

Does anybody know how I can get this to work?

Thanks, Tom.


P.S.

My challenge is to not get my first 1000 beans through asking questions. I hope to be able to answer somebody else's question before that point. :lol:

Not that it's looking likely to happen at the moment. :P

---

### Post by SlidingHorn on 2010-06-07
The icon bar is actually a separate "dock" program...there are a bunch of them out there:

awn (avant window navigator)
cairo
simdock - good for low end machines, as it doesn't require compositing

There are others too if I remember correctly, but those are the more popular ones

---

### Post by SlidingHorn on 2010-06-07
> **SlidingHorn said:**
> The icon bar is actually a separate "dock" program...there are a bunch of them out there:

awn (avant window navigator)
cairo
simdock - good for low end machines, as it doesn't require compositing

There are others too if I remember correctly, but those are the more popular ones

I forgot...

for awn:

```
sudo apt-get install avant-window-navigator
```

for cairo:

```
sudo apt-get install cairo-dock cairo-dock-plug-ins
```

simdock:

```
sudo apt-get install simdock
```

---

### Post by tomnewton on 2010-06-07
Thanks Sliding.

Which one would you suggest? From what I've picked up jest now, AWN seems to be the most commonly used one, however if you know better, please share your knowledge.

Tom.

EDIT: I installed AWN on a whim, but I have no clue how to get it running. Anybody know? Thanks (I will keep trying meanwhile).

---

### Post by SlidingHorn on 2010-06-07
I haven't really used either one since Hardy was new, but I preferred cairo, as I had fewer issues with compiz (which I don't run anymore either)

Info on installing AWN in ubuntu:  [http://wiki.awn-project.org/Installation:Ubuntu#Lucid_.2810.04.29](http://wiki.awn-project.org/Installation:Ubuntu#Lucid_.2810.04.29)

Here's the info on installing Cairo:  [https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

---

