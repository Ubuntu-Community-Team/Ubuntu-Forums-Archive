---
title: "Gaming on a BEOWULF cluster"
date: 2008-07-31
forum: Gaming &amp; Leisure
---

### Post by flytripper on 2008-07-31
This may be  stupid thing to ask as a cluster is only something i have just learned a bit about but i gotta ask.......

A mate of mine works for a pc recycling firm so parts aren't a problem as i can get it all loaned for free.

I am considering building a 4-5 node beowulf just for the sheer hell of it!! I wondered if its possible to get any games running faster or if the cluster only works for the bespoke apps they might run?

please discuss/encourage/heckle/laugh at me/

---

### Post by dfreer on 2008-07-31
I'm thinking a better video card is about the only way you will make games play better/Higher FPS. And from what I understand of a Beowulf cluster, you need programs specifically written to take advantage of multiple CPUS which rules out most games. This is off the top of my head I haven't played around with beowulf cluster concepts for a couple years.

EDIT: Some links:
[http://www.beowulf.org/overview/faq.html#4](http://www.beowulf.org/overview/faq.html#4)
[http://www.phy.duke.edu/~rgb/Beowulf/beowulf_book/beowulf_book/node10.html](http://www.phy.duke.edu/~rgb/Beowulf/beowulf_book/beowulf_book/node10.html)  
[http://www.phy.duke.edu/~rgb/Beowulf/beowulf_book/beowulf_book/node21.html](http://www.phy.duke.edu/~rgb/Beowulf/beowulf_book/beowulf_book/node21.html)  <-- Explains Amdahl's Law

---

### Post by tamoneya on 2008-07-31
most games currently cant take advantage of more than a dual core processor.  Clustering is better for things like blender where you have to render stuff which is highly CPU intensive.

---

### Post by steveneddy on 2008-07-31
Sounds like a cool concept.

Let us know if you get that working.

---

### Post by compiledkernel on 2008-08-01
You might get one heck of a high performance dedicated server out of that, but Im not wholely sure youd get one for a client. 

Hmmmmm...a server that can handle 128 players all at once....only problem is youd have to populate it.

---

### Post by hessiess on 2008-08-01
might make a nice mini-renderfarm ;)

---

### Post by Frem on 2008-08-01
> **compiledkernel said:**
> You might get one heck of a high performance dedicated server out of that, but Im not wholely sure youd get one for a client. 

Hmmmmm...a server that can handle 128 players all at once....only problem is youd have to populate it.

Tribes was doing that eons ago, with a single processor. ;-)
Anyway, you still run into the fact that the server software has to specifically be programmed take advantage of all those networked processors.

---

### Post by compiledkernel on 2008-08-01
Just a pipe dream Frem, not necessarily a reallife application. :)

---

### Post by octobuntu on 2010-03-12
I know it's an old thread, but try this:

[http://www.youtube.com/watch?v=Xn2M1SoVg6U](http://www.youtube.com/watch?v=Xn2M1SoVg6U)

which is from

[http://www.ehu.es/AC/ABC.htm](http://www.ehu.es/AC/ABC.htm)

---

### Post by Pougnet on 2010-03-15
In my opinion, it would be good for cpu intesive tasks (rendering, seeing how fast it can calculate 32 million digits of pi :p) but not for gpu intensive tasks such as games.

---

