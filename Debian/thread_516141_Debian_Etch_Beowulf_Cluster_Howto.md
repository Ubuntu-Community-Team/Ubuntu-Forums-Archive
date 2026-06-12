---
title: "Debian Etch Beowulf Cluster Howto"
date: 2007-08-02
forum: Debian
---

### Post by kevinlyfellow on 2007-08-02
Hello Debianites!

I've just finished a rough draft of a howto build a simple Beowulf cluster using Debian Etch and using open-mpi.

I welcome comments and suggestions, especially since this is just a rough draft and since it was the first cluster I've ever built.  

Hope this helps out at least someone

[http://etchcluster.blogspot.com/](http://etchcluster.blogspot.com/)

---

### Post by dfreer on 2007-08-12
Very interesting, I heard about beowulf clusters about when I first heard about linux, and was always intrigued by the idea.
Now, after reading your article, I have a few questions:
(1) Do the nodes simply add to processing resources (like having a multi-core processor)?  
(2) With NFS, couldn't you pool hard drive space across the nodes as well, or even use some sort of RAID across the nodes? Basically, so instead of just mounting 20 GB /home partition located on the server and sharing this across every node, each additional node would *increase* the size of the common /home.

---

### Post by fjgaude on 2007-08-12
You ask the same questions that came to my mind... I'm sure we can do clustering with our Ubuntu boxes, eh?

Anyway, thanks, kevin, for the detail instructions, easy to follow.

frank

---

### Post by kevinlyfellow on 2007-08-12
> **dfreer said:**
> Very interesting, I heard about beowulf clusters about when I first heard about linux, and was always intrigued by the idea.
Now, after reading your article, I have a few questions:
(1) Do the nodes simply add to processing resources (like having a multi-core processor)?  


Yes, the nodes add processing power or often do all the processing.  This method works great for certain types of computations, especially those that use large matrices.  However, the programs need to be specially built for a beowulf cluster.  I haven't learned how to do the programming yet.  For a cluster that acts like a multi-core processor, take a look at [openMosix]("http://openmosix.sourceforge.net/").  This project is a hacked linux kernel, that allows for things that would normally passed off to different cores to be passed off over the network.  Unfortunately, the devs are calling it quits, but hopefully someone will pick the project up.

> 
(2) With NFS, couldn't you pool hard drive space across the nodes as well, or even use some sort of RAID across the nodes? Basically, so instead of just mounting 20 GB /home partition located on the server and sharing this across every node, each additional node would *increase* the size of the common /home.

Yes, you probably can use a raid across the node.  But, networking doesn't come without a price, and the less packets being sent, then better.  An option is to get extra nics for the nodes and put the nfs server on a separate network than the one being used by the mpi.  Again, networking doesn't come without a price, because that still can cut into the processors time.

I personally wouldn't have use for that since all the nodes I am using have 5 GB hard drives, certainly not worth the networking cost.

---

### Post by kevinlyfellow on 2007-08-12
> **fjgaude said:**
> You ask the same questions that came to my mind... I'm sure we can do clustering with our Ubuntu boxes, eh?

Anyway, thanks, kevin, for the detail instructions, easy to follow.

frank

Your welcome.  I'm sure ubuntu would work more or less the same for clustering.  Again, its really just rsh servers and an nfs server and then a program you build yourself.  I'm not sure if the package names will be the same, but I'd bet that the procedure would be.

---

### Post by trinaryouroboros on 2008-02-11
***I'm resurrecting this post mainly because I've had a massive interest in performing a cluster one day, and I have a bit of a dream that I think many would take with heartfelt sentiment.***

**_My project would be something as follows_:**

[B]2x 2000Mbps PCI NICs in each box, using some decent net balancing

An AMD Phenom, and a couple gigs of RAM in each box

a pack of SATA 3.0Gb/s HDD's in each box set up in RAID-5[/B]

some decent video card in one machine, etc.

**With the 4Gb/s bandwidth to play with, one would surmise that each piece of the quad core's could get decent use, no?**

All this, and an actual decent price to rival some great super expensive servers out there... but, my desire is to **find some way to get Ubuntu to be the beowolf master** in this project.
[B]
*Thoughts, comments?[/B]*

:guitar:

---

