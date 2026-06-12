---
title: "Inspiron 6400n Disk"
date: 2007-09-23
forum: Dell  Ubuntu Support
---

### Post by haelen on 2007-09-23
Hi,

I'm thinking of buying the 6400n with Ubuntu pre-installed. However, I read somewhere that a couple of people have had problems when  they've  needed to update something which requires the (supplied?) CD-ROM, claiming it's been "altered" by Dell.

Is there any truth in this?

TIA,
Tim

---

### Post by ajgreeny on 2007-09-23
Don't know about the specific answer to your question, but if you removed the CD from the sources.list file apt-get or synaptic would stop asking for it, I assume, and just update from the repos like everybody else.

Sorry if that is wrong, but I can't believe there is no way to update without the CD.

---

### Post by haelen on 2007-09-23
That's exactly what I though. I've never had cause to use my Feisty CD again (since the initial install). I've always used the repos.

Maybe it's just a nasty rumour!

Cheers,
Tim

---

### Post by antspants on 2007-09-26
Sometimes you are asked to insert the initial install CD if what you're installing needs some low level programs (maybe a compiler of some sort)

I don't know if by commenting out the CD in the sources.list will force the install to use the repos (never tried it)

Why wouldn't a normal Feisty CD work in that case? Does Dell do something else when installing?

Am thinking of getting a 6400n for my sister with Ubuntu and as I'll be doing the admin, I'd like to know what I might be letting myself in for.

Maybe buy it and do a fresh install?

---

### Post by haelen on 2007-09-26
"Maybe buy it and do a fresh install?"

That's what I was thinking - unless anyone comes up with a clear answer to the rumour I heard :)

Best,
Tim

---

### Post by Linicks on 2007-09-26
I have the UK version of the Dell Inspiron 6400n.

It is pre-installed Ubuntu 7.04 - and I have updated everything and everything *just* works.

[http://ubuntuforums.org/showthread.php?t=544317](http://ubuntuforums.org/showthread.php?t=544317)

Maybe the earlier versions broke with standard updates, but mine has not (including updating the kernel image packages yesterday).

[http://ubuntuforums.org/showthread.php?t=559837](http://ubuntuforums.org/showthread.php?t=559837)

Nick

---

### Post by haelen on 2007-09-26
Thanks for the confirmation Nick :)

Best,
Tim

---

### Post by neptho on 2007-09-27
This is a problem with the 'telephone' game, things always get retold, and done horribly wrong.

The first 6400ns that came out had a typo in the GRUB config file, so when you updated the kernel, they did not want to boot without some rather trivial manual assistance.

Editing this (changing a 0 to a 2 in safe mode,) and rerunning the update utility fixed this problem.

Purple monkey dishwasher.

---

### Post by b3nr on 2007-09-28
> **Linicks said:**
> I have the UK version of the Dell Inspiron 6400n.

It is pre-installed Ubuntu 7.04 - and I have updated everything and everything *just* works.

Nick

Same here, no problems to report at all. Even hibernate and SD Card reader work out of box. Only thing that doesn't is Commercial DVDs. But thats fixable.

---

### Post by antspants on 2007-09-28
Before buying, just be aware that through Dell's pricing policy, UK customers are being ripped off compared to German and French customers.

I posted this .......

[http://ubuntuforums.org/showthread.php?t=561073&highlight=6400n](http://ubuntuforums.org/showthread.php?t=561073&highlight=6400n)

---

### Post by Linicks on 2007-09-28
> **antspants said:**
> Before buying, just be aware that through Dell's pricing policy, UK customers are being ripped off compared to German and French customers.


Yes, well, UK customers get ripped off with everything.  Do a similar comparision with cars, or TV's, or anything else - you will always find we pay about 20%/40% more than anybody else in the world.

So it isn't Dell specific.

Nick

---

