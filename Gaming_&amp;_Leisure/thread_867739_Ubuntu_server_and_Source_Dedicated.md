---
title: "Ubuntu server and Source Dedicated"
date: 2008-07-23
forum: Gaming &amp; Leisure
---

### Post by KristofferAndreas on 2008-07-23
Hi!

first: sorry for my bad english! and im not good explaning...

I and one off my friends have these hobby of hosting CS:S servers... 
today we run to Counter - Strike Source servers on a windows 2k3 computer...
but  we thought off changeing to ubuntu server... cause it dosent have a gui interface and thats more stable and dont need that kind off power...

sorry for tell u all this crap:P

what i really wondered about is... when i run multiple servers... they all need a commandline each...... can someone exsplane how i can do that? so i can run more than one... im also thinking off installing a WebUI to controll easy from many places... ive found hldStart, is this a good one? or can u recomend me a better one?
And... is this hard to insall? i have some exp about this... so i hope it isnt that hard...

and im gonna install torrent flux... is that hard to install?


thanx for every answere...!!!

Kristoffer

---

### Post by bapoumba on 2008-07-23
Moved to Gaming & Leisure.

---

### Post by KristofferAndreas on 2008-07-23
No one that can answere??

---

### Post by dfreer on 2008-07-23
I've installed both torrentflux and ran a Counter-Strike Server off my Debian Lenny system, so I might be able to help. 

As for torrentflux, it's pretty easy to install if you have LAMP (linux, apache, mysql, PHP). I installed it manually, but it's in the repos so you could just apt-get it. Let me know if you have any problems with it specifically.

I'd also recommend checking out torrentflux-b4rt. In fact, if you can do it run them side-by-side and decide which one you like best.

As for the counter-strike servers, one extremely simply way to run multiple servers is to install each to it's own directory. Start here:
[http://www.srcds.com/db/engine.php?subaction=showfull&id=1098643920&archive=](http://www.srcds.com/db/engine.php?subaction=showfull&id=1098643920&archive=)
And repeat the process each time to a different directory. 

Of course, this ends up much more Hard Drive space, so the best solution would be to check out the forums on srcds.com to see how you can best optimize running multiple servers on the same machine.

EDIT: BTW, don't be impatient and expect an answer when the threads only 7 hours old ;)

---

### Post by KristofferAndreas on 2008-07-23
Thx duude!

next time im gonna be much more pasient...

ive install all the servers... so im gonna do what u said and use the screen script... :D

i check out the torrent flux too!
 
btw is there anyone who can recomend a good Web UI for multiple CS:S servers or is the hldStart best? i dont now much about this... but what i realy want is one with a very powerful controllpanel...

Thx

Kristoffer

---

