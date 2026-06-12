---
title: "Immense amount of lag in Quake III"
date: 2009-03-07
forum: Gaming &amp; Leisure
---

### Post by kaldor on 2009-03-07
While playing Quake III Arena, I get extremely bad ping and lag. This does not happen with any other game I play (Jedi Outcast/Academy, Quake II, Tremulous) and it is quite annoying. I originally thought it might be an internet problem, so I tested something out; I went to my old PC (not an amazing machine) and got a ping of 60 on a server. I then went to my new computer (the one I am having this problem on) and my ping jumps from 280 to 500 every few seconds. It is unplayable.

What is causing this? It is not an FPS problem, just really really bad lag. Like I said, I get perfectly fine ping in all other games I play.

---

### Post by LegendofTom on 2009-03-08
Are there any other processes running that could be slowing down your machine?

---

### Post by Ferrat on 2009-03-08
> **LegendofTom said:**
> Are there any other processes running that could be slowing down your machine?

that doesn't really affect ping unless it's really really bad and then you would have noticed it before, sounds more like a sync problem if he doesn't have any problems with other games and there truly is nothing wrong with the connection, my first question on this would in other case usually be do you use wireless?

---

### Post by kaldor on 2009-03-09
Yes, I do use wireless.

But I assume that has nothing to do with it since all other games run perfectly fine.

---

### Post by epitaph on 2009-03-09
Which client are you running?

If you are running vanilla, try using ioquake3 or ChallengeQuake3.

You could try lowering your maxpackets and your rate I suppose.

---

### Post by kaldor on 2009-03-11
I have tried altering maxpackets and rate.

I am running vanilla 1.32 (latest)

What is ioquake3?

---

### Post by epitaph on 2009-03-11
[http://www.ioquake3.org/](http://www.ioquake3.org/)

Essentially it is a replacement for the iD vanilla quake3 client. There is also ChallengeQuake3.

The other games you listed included some games that were based off the quake3 engine, though I can't remember of they use 27960 as their default port.

It may be worth seeing if servers running on non-default ports (and preferably those out of the range) would still exhibit the same lag. Perhaps some kind of prioritizing or shaping is occurring with regards to your UDP data over port 27960.

When you are lagging in quake3, try to ping and traceroute the server's IP in a terminal.

```
ping <IPHERE>
traceroute <IPHERE>
```

That will show where the lag is happening (if it's not local on your computer).

---

