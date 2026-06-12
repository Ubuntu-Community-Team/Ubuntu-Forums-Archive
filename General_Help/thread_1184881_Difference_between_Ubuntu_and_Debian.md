---
title: "Difference between Ubuntu and Debian"
date: 2009-06-11
forum: General Help
---

### Post by frindly on 2009-06-11
hello,
what are the differences between ubuntu 8.04 installed from live cd and debian lenny (installes from network installation cd)?
i dont mean the graphical enviroment. 
i am interested in the consolen tools like dd, top, grep, awk, sed etc.
are these tools are the same at ubuntu, or are some tools were removed so that ubuntu is small enough for one live cd?
is the administration of an ubuntu (installed from live cd) the same like debian?
or are here some programmes missing?

---

### Post by LKjell on 2009-06-11
How shall we measure differences? Obviously there is a difference between those two. But since Ubuntu is base on Debian there is a time they are alike. Which are between when a new Ubuntu is released (Alpha/Beta). This is on package level not what is really installed. If you go to DistroWatch.com and press on Ubuntu and Debian there is some columns where you can compare the installed version of which tools they use. Other than that it is possible to install all the tools Debian use on Ubuntu and vice versa. That is the freedom you have.

---

### Post by kuja on 2009-06-11
The differences for admin tools between Ubuntu and Debian are minimal. If you're used to doing admin stuff in Ubuntu you'll do well in Debian and vice versa. You might notice the occasional difference every now and again, but in those cases it's generally packaged and can easily be installed.

---

### Post by Celauran on 2009-06-11
As I understand it, the bulk of the differences between the two revolve far more around release cycles and ideology than they do around actual software.

---

### Post by lamego on 2009-06-11
The console tools that you list are base utilities common to all linux distros (and some Unixes also), you will find those on Ubuntu, Debian, Fedora, etc...

---

### Post by Anzan on 2009-06-11
Yes, the difference have to do with the stated intentions of each distribution.

Debian is "the universal operating system" and aims to provide free software for every architecture possible.

Ubuntu is aimed at providing the best possible user experience on desktop systems, netbooks, and servers.

The GNU tools are all here. But so too are particular refinements to the GUI, especially in GNOME and Xfce. (I don't know much about Kubuntu or KDE.)

It's Debian given a particular focus. And a great community and commercial sponsor, Canonical.

---

### Post by Sinkingships7 on 2009-06-11
Debian focuses on stability, while Ubuntu is more bleeding-edge. You'll find newer software with Ubuntu, and older (tested and true) software with Debian. Essentially, the same software can run on both, so the difference lies in the repositories.

---

### Post by WatchingThePain on 2009-06-11
The best way to find out is to try both.
I did.

When you try Debian it becomes obvious that Ubuntu comes from that.
What I liked about Debian was the stability.
I don't know how to describe the difference.
Ubuntu is more multimedia ready? IDK.

It's a bit like when a yogi meditated for years and apparently saw God.
When asked what it was like he never answered because no words could describe the experience ;).

---

### Post by frindly on 2009-06-13
> **LKjell said:**
> How shall we measure differences? Obviously there is a difference between those two. But since Ubuntu is base on Debian there is a time they are alike. Which are between when a new Ubuntu is released (Alpha/Beta). This is on package level not what is really installed. If you go to DistroWatch.com and press on Ubuntu and Debian there is some columns where you can compare the installed version of which tools they use. Other than that it is possible to install all the tools Debian use on Ubuntu and vice versa. That is the freedom you have.

Hello,
i mean the difference between the command line interface programms for administration. I know that the graphical programmes are different, or the version of the programs. But the non gui tools, are they the same. I ask, because there anre much programmes on the live cd (gnome, openoffice, evolution, fspop, gimp, firefox eg) is there enough space left for the cli programmes? Or did they removed some of the basisc programmes because the main user of Ubuntu use the graphical interface?

---

### Post by frindly on 2009-06-13
> **kuja said:**
> The differences for admin tools between Ubuntu and Debian are minimal. If you're used to doing admin stuff in Ubuntu you'll do well in Debian and vice versa. You might notice the occasional difference every now and again, but in those cases it's generally packaged and can easily be installed.

Ok. it means, when i dont install other packages in Debian (only standart installation), the tools are the same like in Ubuntu (installed from live cd) ?

---

### Post by frindly on 2009-06-13
> **lamego said:**
> The console tools that you list are base utilities common to all linux distros (and some Unixes also), you will find those on Ubuntu, Debian, Fedora, etc...

Ok. How much space do the basic tools need? 20MB? 100MB? Did somebody know?

---

### Post by keypox on 2009-06-13
I hate to say it but both are so far behind windows.  It sucks to say but its the truth. 

Cutting edge is more ubuntu, BUT ubuntu is not cutting edge...

---

### Post by QIII on 2009-06-13
In what way are they "behind" Windows?

They are buses running on completely different routes.

---

### Post by chronographer on 2009-06-13
It comes down to this. Debian stable is very stable. It is good for web servers and other systems which should be up 99.99% (or better) of the time. 

Debian testing is less stable, it has more recent packages which have known bugs in them but should be pretty good to go.

Finally Debian Sid is called unstable. Packages are prone to big changes and you should be prepared for trouble.

Ubuntu is built on Debain Sid... This means we get bleeding edge packages i.e. the latest software with some instability. That's all. For all intents and purposes if you can handle Ubuntu, you will find Debian identical if not very familiar. 

I like Debian but Ubuntu is better for a desktop operating system imho.

---

### Post by Sinkingships7 on 2009-06-13
> **keypox said:**
> I hate to say it but both are so far behind windows.  It sucks to say but its the truth. 

Cutting edge is more ubuntu, BUT ubuntu is not cutting edge...

Maybe. This depends on what light you look at the situation in. If you mean Windows is a more advanced operating system, then I'd have to disagree with you on many levels. If you measure "cutting edge" by the software that's written for an operating system, then we'd have to compare the quality of software, not of the operating system itself.

---

### Post by frindly on 2009-06-13
> **keypox said:**
> I hate to say it but both are so far behind windows.  It sucks to say but its the truth. 

Cutting edge is more ubuntu, BUT ubuntu is not cutting edge...

when i compare linux and windows, i must say.... linux looks better. linux has excelent software. and... linux runs faster on the machine. you need one cd ob untuntu and have everything you need. operating system, office, mail program, internet program, photo editing, burn software. for this you need with windows lots of gb harddisk space.
ubuntu is for free, and lots of frindly helping people.

what is on windows better???

---

### Post by snowpine on 2009-06-13
Really you could answer this question yourself by burning two live cds and spending some time with each... 

You will find the command line interfaces and tools are pretty much the same, the biggest difference being that Debian uses su (but you can enable sudo) and Ubuntu uses sudo (and it is illegal to enable su). Some people are scared off Debian because of their strict open source policy, but that's a minor issue because it's easy to add the nonfree stuff after you install. Also the "Debian has old packages; Ubuntu is bleeding edge" thing is a myth created by users who are only aware of the Debian stable branch (imho most users switching from Ubuntu should use testing or sidux).

For me, the #1 and #2 reasons to choose between Ubuntu and Debian are the release cycle (Ubuntu has timed 6-month releases; Debian has stable, unstable, testing) and the communities (ask a stupid question on the Debian forums and they will swear at you, ask one here and fluffy bunnies will hold your hand and tell you it's ok). 

The bottom line is that they are 95% the same. An experienced user of Ubuntu can transition to Debian easily, and vice versa.

---

### Post by WatchingThePain on 2009-06-13
> **frindly said:**
> when i compare linux and windows, i must say.... linux looks better. linux has excelent software. and... linux runs faster on the machine. you need one cd ob untuntu and have everything you need. operating system, office, mail program, internet program, photo editing, burn software. for this you need with windows lots of gb harddisk space.
ubuntu is for free, and lots of frindly helping people.

what is on windows better???


Well for one thing the Viruses are better.

---

