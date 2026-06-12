---
title: "Trying to find a way to 3D map my MUSH"
date: 2008-07-15
forum: Gaming &amp; Leisure
---

### Post by Th3Professor on 2008-07-15
**3D Map Drawing for "mud", "mush", "mu*", etc.** 			
 			 			 		   		 		 		I'm looking for one... to map out text-based environments for a 3d visual reference map. Any ideas where to find a program that does that? (Hopefully easily does that.)

Thanks! :smile:

---

### Post by Vadi on 2008-07-15
[Pandora mapper]("http://code.google.com/p/pandoramapper/")

---

### Post by Th3Professor on 2008-07-15
Ah thank you... though I did the steps provided to get it installed (even provided for Ubuntu within the docs) but it didn't seem to want to install. Any ideas?

I did exactly what it said, installed the required q-something, went to the src directory and ran qmake or gmake or something like htat, then make... which seems a bit different then how I thought apps were installed when done manually, though I followed their steps anyway, yet it wouldn't install. :(

Was I missing something?

Or is there possibly another program?

---

### Post by Vadi on 2008-07-16
Don't know of another program, but Pandora most likely won't work out of the box anyway without modifying the sources - it's designed for some special mush which gives you exits already in xml format. Sorry

---

### Post by Th3Professor on 2008-07-16
Ah bummer.

When it actually works... does it let you create 3D maps without having to directly link it to that particular non-MUSH game?

If it still works as a general 3D mapping utility in a way that can be applied to any text environment mu*, then it should be fine. However... still havin' probs installing it.

Do you (or anybody) have any pointers on properly installing it?

Beyond that program - does anybody else have any suggestions or recommendations?

Thanks! :D

---

### Post by Vadi on 2008-07-16
You could contact the projects author for help. I don't know if any other ones, sorry. I found a simple ansi map to be sufficient for my purposes, and I just like autowalkers more.

---

### Post by Th3Professor on 2008-07-16
I should clarify what I was looking for, sorry 'bout being vague.

My family and I run a private MUSH, or "multi user shared hallucination/habitat", or text-based online/interactive gaming environment that consists of going from room to room with n, s, e, w type key-stroke movement (north, south, etc.), or even up and down in cases where the text description of one "room" says an elevator goes up/down or stairs, ladder, rope, etc. Perhaps the majority of it is on one level, though there is an increasing amount of "walkable" type areas above and below that ground level.

I suppose a 2D mapping program could work with the obvious limitations (XY coords. instead of XYZ), and a new map could be created for each level. However, I'm hoping to be able to utilize a 3D program that will help in transferring those rooms/levels from simple text to a graphical representation of that text.

Currently, there is no actual text-based map, so there is nothing to simply be "converted" over. The map will actually have to be manually created from scratch.

The idea is, we will open up both programs - the MUSH client with the text environment and a 3D mapping program - and as we "text walk" through the MUSH's environment we create new rooms in X-direction from the previous rooms within the 3D mapping program. It's a slow process but well worth it when the map is complete.

---

### Post by Th3Professor on 2008-07-26
Blender works... though, is there something more simplistic for creating 3D map environments? (Something that helps create them faster?)

Simple is ideal... like with each room/area being a basic "cell" (referential object or point).

An XYZ would be perfect.

---

### Post by Vadi on 2008-07-27
Check back with KMuddy in like half a year or so. We'll be working on a 3d mapper for it.

---

### Post by Th3Professor on 2008-07-27
> **Vadi said:**
> Check back with KMuddy in like half a year or so. We'll be working on a 3d mapper for it.

We? You're part of the kmuddy team? Cool. :) It's a nice client.

Until KMuddy's got that going, any ideas on make-shift alternatives for the time being?

---

### Post by Vadi on 2008-07-27
Well, anyone could be part of Kmuddy team! But yes I do contribute.

I don't know, not too experienced with 3d modelling. I suppose if you simply make 2 models, a box and a line, and just ctrl+c and ctrl+v them in proper places, that would do...

---

### Post by Th3Professor on 2008-07-29
> **Vadi said:**
> Well, anyone could be part of Kmuddy team! But yes I do contribute.

I don't know, not too experienced with 3d modelling. I suppose if you simply make 2 models, a box and a line, and just ctrl+c and ctrl+v them in proper places, that would do...

If the kmuddy team needs someone to beta-test that 3D mapping addition, I'd be glad to. My family and I have a pretty extensive MUSH that is always under experimentation and testing of new features and such.

I've tried the ctrl-c and ctrl-v of the basic box and line models. It works pretty well, though after discovering Blender, and after doing the box+line approach for a while I realized that with the time I was putting into copy/pasting them in proper places, I could do the same thing copy/pasting with 3D models in Blender. Though the concept you mentioned, box and line, is a very effective tool in mapping out a text environment. :)

---

### Post by Vadi on 2008-07-29
Okay, I'll let you know when kmuddy has the mapper finished and usable.

---

### Post by Th3Professor on 2008-07-29
> **vadi said:**
> okay, i'll let you know when kmuddy has the mapper finished and usable.

:-)

---

### Post by Th3Professor on 2008-08-04
> **Vadi said:**
> Okay, I'll let you know when kmuddy has the mapper finished and usable.

Is there an email list or some way to receive updates or contact for kmuddy progress?

If there is, my email's in my signature. Thanks! :D

---

### Post by Vadi on 2008-08-04
No mailing list, but it'll surely be posted on kmuddy.com/mercuryboard

---

### Post by Th3Professor on 2008-08-05
excellent! i'll check that out.

---

