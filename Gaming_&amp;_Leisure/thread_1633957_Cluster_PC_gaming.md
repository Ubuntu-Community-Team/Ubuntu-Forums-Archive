---
title: "Cluster PC gaming?"
date: 2010-11-29
forum: Gaming &amp; Leisure
---

### Post by nekronuke on 2010-11-29
Howdy y'all i was searching around the internet and wanted to find a way to make my PC better without spending a heap of cash, cuz im a gamer, and i fix computers in my area, i figured the might be a way to make computers together, and before i found out what that beowulf clustering is, i called it reverse networking.

Now, can i get some clear instruction please? i know i probably sound dumb, but i just recently heard about linux, and it sounds like a dream. so, any help would be nice-

an overview of what to do (how to set up the cluster, and if i can run games from windows on the master pc and have it still work with the slave PCs, and if i can use different models of PCs in a cluster. thanks in advance!

---

### Post by mastablasta on 2010-11-30
cluster? you mean you would put a lot of PCs together to do one process which will be to run a game or what?
 
or perhaps what you are talking about is just gaming over the network?
 
Linux is not really for gaming. i mean there are games just not the latest ones that are in windows. if you want to run windows server and then connect other PC to it (LAN), you can do that but still your game needs either a Linux client or be able to fully run in WINE (which will "emulate" windows).
 
It's also possibel the other was arround as long as windows have the client for the game. for example Smokin' Guns have client and sevrer for both systems.

---

### Post by cascade9 on 2010-11-30
From what I know...not a bad idea, but it wont fly. At all.

2 answers from 2006 are still fairly current- 

[http://ubuntuforums.org/showthread.php?t=218822](http://ubuntuforums.org/showthread.php?t=218822)

[http://ohioloco.ubuntuforums.org/showthread.php?t=290280](http://ohioloco.ubuntuforums.org/showthread.php?t=290280)

---

### Post by rizzeh on 2010-11-30
Why not? :)
[http://www.shadowflux.com/xbox.html](http://www.shadowflux.com/xbox.html)

---

### Post by thatguruguy on 2010-11-30
> **rizzeh said:**
> Why not? :)
[http://www.shadowflux.com/xbox.html](http://www.shadowflux.com/xbox.html)

Because running a game and compiling a kernel are two different things.

---

### Post by Grenage on 2010-11-30
> **nekronuke said:**
> Howdy y'all i was searching around the internet and wanted to find a way to make my PC better without spending a heap of cash, cuz im a gamer, and i fix computers in my area, i figured the might be a way to make computers together, and before i found out what that beowulf clustering is, i called it reverse networking.

Now, can i get some clear instruction please? i know i probably sound dumb, but i just recently heard about linux, and it sounds like a dream. so, any help would be nice-

an overview of what to do (how to set up the cluster, and if i can run games from windows on the master pc and have it still work with the slave PCs, and if i can use different models of PCs in a cluster. thanks in advance!

Do it.  It'll almost certainly fail at doing what you desire, but you'd learn a lot.  That said; with no Linux experience, it might be a rough ride.

---

### Post by dfreer on 2010-11-30
Also, you will run into bandwidth issues between the nodes in the cluster. You'll would probably need specialized motherboards (read: expensive) that have a way of sharing the PCI/HT bus in order to see any sort of performance increase.

Beyond that, most games run with 1 or maybe a few more threads. 1 thread cannot be worked on in parallel, so your cluster of say 20 computers would only be able to utilize maybe 1-4 machines.

As far as graphical performance, in order to play any newer games you will need the newer technology contained in the newer cards. You may be able to combine multiple video cards across your cluster with a specialized interface (again expensive), but that would only give you access to raw number crunching power, and no access to those new technologies.

---

### Post by rizzeh on 2010-11-30
> **thatguruguy said:**
> Because running a game and compiling a kernel are two different things.

One could, for example, let Chess AI calculate the moves on a cluster - it'll count as playing :P

---

### Post by thatguruguy on 2010-11-30
Sure.  If what he means by "gaming" is that he wants to play chess.

---

