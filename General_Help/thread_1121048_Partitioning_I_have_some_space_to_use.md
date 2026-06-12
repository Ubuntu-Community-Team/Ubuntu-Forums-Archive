---
title: "Partitioning: I have some space to use"
date: 2009-04-09
forum: General Help
---

### Post by Kivech on 2009-04-09
Hi all,

I just got myself some new disks because the ones I had were starting to show errors and needed replacement. Nowadays those disks are so dirt cheap that I bought myself a nice bunch: three Maxtor SATA disks of 250 Gb each.
They are all nice and shiny :p

Now, my usual patition setup is like this:

/boot
/swap
/
/var
/tmp
/usr
/home

I used to spread them over the original 180 Gb disk I had at first, but now, obviously, I have an abundance of space to my disposition and need a bit of advice on how to divide that.

I am not someone who downloads a lot or who rips tons of disks. I have a decent photo collection, work a lot on my pc (so lots of documents, presentations and such) and want to dedicate part of my new setup to some scientific software (maths, geology, programming, translating and seismology software). I'll probably set up a few games for the kids as well, but that will never take a lot of space with what I have in mind.

So having 3/4 of a Tb, I was initially thinking that it might be a good idea to use two disks for the system and one solely for backups. System reliability and security are pretty important for me since both me and my wife work on this PC. On the other hand, having the habit of making regular backups on disks I can imagine that it is also a bit of a shame to dedicate a full 250 Gb disk just for this purpose.

Anyway, I want a pretty professional setup (originally I have once, in a long forgotten past, been an Unix admin) because I like how nicely organised that is and it makes maintenance easier for me.
How would you guys, who know a bit what makes sense and what doesn't, utilise my 750 Gb?

I'm open to any ideas and suggestions. For me the most important things are easy maintenance and not having to worry too much about having to adjust partitions due to lack of space. I'd rather use a bit too much space than too little.
I do think a full disk for just the /home dir wouldn't be a bad idea though. I mostly have my mind set about that one. The main thing I need to decide upon is how much space I should allocate to which directory. Or whether I should specify even more in detail what goes where.

Anyway, you guys get the idea. Again, any ideas and thoughts are welcome.

Thanks in advance for all your help.

Kivech

---

### Post by lisati on 2009-04-09
Ah, that reminds me, I have an external NTFS-format HDD that needs some attention (file system knobbled with directory entries pointing in the "wrong" place, amongst other things, and possibly some data that I don't have stored elsewhere)


I'd probably go for one HDD being primarily a backup device, the other divided between different kinds of files and documents, and the 180Gb device holding your "working copies".

---

