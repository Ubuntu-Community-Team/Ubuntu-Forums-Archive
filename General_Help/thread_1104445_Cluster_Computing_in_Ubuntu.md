---
title: "Cluster Computing in Ubuntu"
date: 2009-03-23
forum: General Help
---

### Post by NekoMaster on 2009-03-23
Ok I dont know where to put this so I plopped it here.
Anyways I have a lot of music to convert and even with a dual core cpu it will take me at least all day. SO what I want to do is connect to PC's running ubuntu together via Gb Ethernet to use the Power of 2 Dual Core PCs to convert the music.

Is there any way i can do this? I would also like to know this so I can maybe one day just assemble a bunch of shitty PC's and cluster compute to get lots of power :D

---

### Post by sdennie on 2009-03-23
Unless you find a way to keep both cores busy, you are probably only using one to do your work.  You can probably dole out your work to other machines but, it may not make it faster because of the network latency.  Essentially, you don't have a cluster and you don't need one.

---

### Post by mb_webguy on 2009-03-23
Clusters and distributed computing are only effective for problems that can be split into numerous discrete chunks.  And since no network connection is anywhere near as fast as an internal bus, the size of the problem has to be sufficiently large that the advantage of simultaneous processing is greater than the disadvantage of network latency.

Furthermore, most programs still aren't written to take advantage of multiple cores on one computer, much less distributed across multiple computers on a network.

The bottom line is that even *if* you could set up a cluster to convert your media, by doing so you'd be reducing performance rather than increasing it.

---

### Post by NekoMaster on 2009-03-27
> **mb_webguy said:**
> Clusters and distributed computing are only effective for problems that can be split into numerous discrete chunks.  And since no network connection is anywhere near as fast as an internal bus, the size of the problem has to be sufficiently large that the advantage of simultaneous processing is greater than the disadvantage of network latency.

Furthermore, most programs still aren't written to take advantage of multiple cores on one computer, much less distributed across multiple computers on a network.

The bottom line is that even *if* you could set up a cluster to convert your media, by doing so you'd be reducing performance rather than increasing it.

Sure, anyways, the program i use for converting audio (dbpoweramp) has the ability to convert 1 audio file per core, so with a dual core, thats 2 audio files at a time, a quad core can obviously do 4, and more the likely the Intel i7 can do 8.

---

### Post by mb_webguy on 2009-03-28
> **NekoMaster said:**
> Sure, anyways, the program i use for converting audio (dbpoweramp) has the ability to convert 1 audio file per core, so with a dual core, thats 2 audio files at a time, a quad core can obviously do 4, and more the likely the Intel i7 can do 8.

Sure, anyways, this isn't the same *at all* as distributed or cluster computing.  Multiple cores are contained on the same CPU, using the same high-speed bus.  Clusters are separate computers linked together by much, much, *much* slower connections with lots of overhead.

Think about it this way...  Multi-core computing is like a chess master who is able to consider several different moves at once.  Cluster computing is like having several different chess players in a room, cooperatively playing chess, and each having to communicate to each other which move they are individually considering, and then communicating the anticipated results of those moves.  The chess master is going to be faster at playing a game of chess, because he doesn't have to talk to a roomful of other people to decide each move.  Each player you add to the cooperative game is actually going to slow down the game because the amount of communication required increases exponentially.

On the other hand, suppose you're trying to figure out the average number of turns in a game of chess.  To do that, you'd have to play a lot of games of chess, count the number of moves, add them together, and divide by the number of games to get the average.  The chess master can play a single game of chess extremely fast, but if he has to play 1000 games of chess, it's still going to take him a while.  On the other hand, if you had enough players to play those 1000 games at the same time, it would go much faster.  And since each of those games is independent of each other, and the players only have to communicate a single, simple piece of information -- the number of moves it took to complete their own game -- there's not much communication overhead.

Writing software for clusters or distributed computing systems is not the same *at all* as writing for multiple cores.  For the latter, you essentially just have to write your program to use multiple threads.  For the latter, you're dealing with network protocols and sending data between identical programs running on different CPUs.  The two may seem like similar concepts in that you're dividing up the work, but they're actually very different.

---

