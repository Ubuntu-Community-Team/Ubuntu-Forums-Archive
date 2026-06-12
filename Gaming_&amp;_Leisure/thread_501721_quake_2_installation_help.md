---
title: "quake 2 installation help"
date: 2007-07-15
forum: Gaming &amp; Leisure
---

### Post by itzpapalotl on 2007-07-15
Okay. okay I give.. How do I get from the point where i have clicked on the quake2 package and downloaded it, to the the point where I am dealing out frags. I have the binaries. Lots and lots and heaps of mods all on my xp drive partition. What so I do with it?

there are no new icons in the game menu after downlaoding. I found quake2 in /usr/games but nothing else seems to be going on.

So what comes next?

---

### Post by cjl2301 on 2007-08-18
First grab both the quake2 and quake2 data packages.

Once they are installed this directory will be created:

/usr/lib/games/quake2

under you will see:

/usr/lib/games/quake2/baseq2
/usr/lib/games/quake2/ctf

Copy the contents of Install/Data/baseq2 and install/Data/ctf from the install CD into each of those 2 directories in /usr/lib/games/quake2.

then run /usr/lib/games/quake2/quake2.real to start.

hope this helps - thats what worked for me!

---

### Post by Beaucephus on 2007-08-19
Hmmm... I'm trying this now, but I dont have a ctf directory on my install cd.

What up with that?
EDIT: Game runs but with no sound
EDIT: Solution found in other thread.  Run as 

```
quake2 +set snddriver ao +set snddevice oss
```

---

### Post by TheForkOfJustice on 2007-08-19
I wonder if I should risk asking you guys for the required files to run the thing.  I wanna play :(

Don't want to rub the mods the wrong way.

---

### Post by cjl2301 on 2007-08-19
> **TheForkOfJustice said:**
> I wonder if I should risk asking you guys for the required files to run the thing.  I wanna play :(

Don't want to rub the mods the wrong way.

You can still purchase Ultimate Quake for only $19.99.

[http://www.amazon.com/PC-Ultimate-Quake/dp/B000GSNZNK/ref=pd_bbs_sr_1/102-8375163-7120947?ie=UTF8&s=software&qid=1187581642&sr=8-1](http://www.amazon.com/PC-Ultimate-Quake/dp/B000GSNZNK/ref=pd_bbs_sr_1/102-8375163-7120947?ie=UTF8&s=software&qid=1187581642&sr=8-1)

---

### Post by itzpapalotl on 2007-08-27
Okay... That sounds good I'll give it a go tonight..
Thanks

---

