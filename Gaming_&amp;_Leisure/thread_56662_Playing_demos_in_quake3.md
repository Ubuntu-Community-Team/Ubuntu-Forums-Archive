---
title: "Playing demos in quake3"
date: 2005-08-13
forum: Gaming &amp; Leisure
---

### Post by crane on 2005-08-13
I have an interesting problem I have been trying to fix on and off for some time now. I have a demo record script that I use to record some of the games I play. The only problem is they will not play/ I get the error "couldn't open demos/foo.dm_68.

I have checked all permissions and all seems well. I have put the demo in various places with no luck. Funny thing is that the one demo that comes with the game will play. Any added will not. Does anyone have any ideas?

 I'll keep working on it and ppost if I find anything.

Thanks for any input!

---

### Post by crane on 2005-08-13
OK I figured out a couple of things.
First the four demo that comes with the game is located in pak8.pk3.
Now if I put my demos in the pak8 file (which is a zipped archive file I can watch them.
 Thats great, but, this brings in another problem. If I do this and try to join a Q3 serverthat is running punkbuster I will be kicked for having improper pak files. [-X 

 Now I just have to get around this issue.
Is there a way to make a directory, link it to another directory (say ~/.q3a/baseq3/demos), then move it into the pak file without losing it's link? I'm not sure this will work but it's worth a try.

---

