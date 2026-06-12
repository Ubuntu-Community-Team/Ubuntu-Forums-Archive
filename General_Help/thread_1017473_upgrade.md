---
title: "upgrade"
date: 2008-12-21
forum: General Help
---

### Post by garrynigel on 2008-12-21
hi
i  have decided to upgrade my machine from 1 gb ram to 3 gb ram. and also increase my hard disk space presently i have 160 gb but i use 40 for linux and remainin for windows but what d heck i can access windows docs thru linux..but now i already have ubuntu 8.10 installed..with 2 gb swap area and 8 gb root and around 24 gb for home... can i  work linux .. i mean the swap area has to generally be 2wice ur ram space.. is it possible to increase the size of the swap and root...as well as home.. withuot affecting the data iv already installed or il have to start from scratch by installing linux all oer again and install all the sotwares thru the apt get command.... just curious.. i knw dis is not possible in windows but i was just thinkin if its possible in linux..
please help...

---

### Post by SPr on 2008-12-21
With 3GB of RAM you'd need to run some very memory intensive programs before swap is used. Don't bother resizing the swap partition. Partitions can be resized without reinstalling but there is a risk of losing data so make a backup of the entire hard drive so it can be restored. Hmmm, I was going to suggest a backup program but I've just realised it doesn't work if the partitions change size between the image being made and being restored - which makes this post kind of pointless...

---

### Post by jimmy the saint on 2008-12-21
These days, with memory being measured in gigabytes not megabytes, the only reason to have a large swap space (for normal home use) would be for hibernation.  Unless you intend to hibernate your computer, there is probably no need.

---

### Post by garrynigel on 2008-12-21
thanx guys 
 just curious u knw ... coz wen i first tried to dual boot .. i had amazing problems  the grub was not gettin installed and al sorts of weird things.. finally got that thing done... and just tht might need an ugrade for fifa.. tht swap was required by linuxfor some kernel purpose and had to do with the memory ram.. little cautious bfore doin sometin.. wid linux.. 
 by d way hibernate is to save the memory power like in windows i s cald standby rite


garry

---

