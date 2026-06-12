---
title: "Remove Dellfand"
date: 2008-08-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jdorenbush on 2008-08-26
I installed Dellfand yesterday and everything seemed to be working fine. I set my temperatures to similar settings that I've used in i8kfangui on Windows XP. Then my fans starting fluctuating like crazy. High to off over and over and over again.

So what I want to do now is just remove Dellfand so it isn't controlling my fan speeds at all. I am having a hard time removing it though (keep in mind, I am a Ubuntu noob)

I tried: '[FONT="Courier New"]sudo apt-get remove dellfand[/FONT]' This is what happened.

[FONT="Courier New"]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package dellfand[/FONT]

Any help removing this is appreciated, or just help figuring out how to fix the fluctuating. Also, is there fan control software for Ubuntu with an interface and temp display?

---

### Post by Cheesehead on 2008-08-26
'apt-get remove' only works if you used 'apt-get install' to install it.

Did you follow the instructions on using dellfand? Particularly that it requires root, and that you can set temp thresholds for low/medium/high speed operations?

To remove it:
On the command line, type 'which dellfand' to get the path to the executable.
Type 'sudo rm path/to/dellfand' to get rid of it. Obviously your path will be different.

---

### Post by jdorenbush on 2008-08-26
My problem was that I wasn't at ROOT :\

Anyways, these are the settings I have.

dellfand 1 2 29 33 40

It is still doing weird things, like it'll kick into high for about half a second (or less) then shut right off again.

I went ahead and removed it based on the instructions you gave me Cheesehead (thanks btw). However my fans are still fluctuating. Its like the app is removed, but the fan settings haven't changed. Keep in mind, my fans DON'T do this in Windows, so it isn't a hardware issue. 

Not only is this annoying having your fans go on and off like this, but it is also freaking me out - I feel like my laptop is going to overheat or the fans will burn out or something.

---

