---
title: "Photo transitions or morphing?"
date: 2006-06-22
forum: Desktop Environments
---

### Post by dcraven on 2006-06-22
Does anyone know a relatively non-painful way to take a bunch of like photos and create a sort of "morphing" animation that shows progress from the first photo to the last? I'm sure there is a neato solution, but I have no idea what it is.

I hope I explained what I would like clearly enough :).

Thanks,
~djc

---

### Post by Nonno Bassotto on 2006-06-22
try gtkmorph in the repos.

---

### Post by LKRaider on 2006-06-22
There's gtkmorph (and xmorph, which can be run as a Gimp plugin) on Synaptic.

A Gimp tutorial:
[http://www.gimptalk.com/forum/topic/Morphing-Images-4391-1.html](http://www.gimptalk.com/forum/topic/Morphing-Images-4391-1.html)

There's also a tool called XMRM (not on synaptic), but seems a bit complex:
[http://www.cg.tuwien.ac.at/research/ca/mrm/xmrm.html](http://www.cg.tuwien.ac.at/research/ca/mrm/xmrm.html)
[http://www.linuxfocus.org/English/September2001/article139.shtml](http://www.linuxfocus.org/English/September2001/article139.shtml)

---

### Post by dcraven on 2006-06-22
gtkmorph is ugly as sin, but it got the job done :). I couldn't get it to morph between several images though, so I had to settle with two.

Thanks for the ideas guys!

Cheers,
~djc

---

### Post by aysiu on 2006-06-22
Maybe ImageMagick has something. I know it has *animate*...

---

### Post by dcraven on 2006-06-23
[QUOTE=aysiu]Maybe ImageMagick has something. I know it has *animate*...[/QUOTE]
I actually ended up using ImageMagick's *convert* command to add a few seconds pause to the first and last frame. Worked quite well.

Cheers,
~djc

---

