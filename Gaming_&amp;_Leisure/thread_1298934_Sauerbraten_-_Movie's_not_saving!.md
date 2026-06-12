---
title: "Sauerbraten - Movie's not saving!"
date: 2009-10-23
forum: Gaming &amp; Leisure
---

### Post by kvarley on 2009-10-23
When I'm in sauerbraten on a bot match I set a movie to record using:
> 
movie /home/starcube/Videos/tester.avi

Then I stop the movie with:

> movie

It says movie halted or something.

When I go to the directory /home/starcube/Videos/ the video isnt there!

If I use:

> locate tester.avi

I find nothing, therefore I think that sauerbraten isnt creating the video, is there a different way I have to stop the movie?

---

### Post by Sindwiller on 2009-10-23
I'm not sure if you really are supposed to type 'movie' a second time; at least it's not mentioned [in the Wiki page]("http://sauerbraten.org/docs/game.html#movie_recording"). What it mentions though is that the movie file is stored as <filename>XXX.avi if it exceeds 1 GB, where XXX is the number of the chunk, eg. 001, 002, and so on.

Otherwise, #sauerbraten @ irc.quakenet.org

---

### Post by tkmn on 2009-10-23
When I tested it the movie was saved in the **~/.sauerbraten/** folder

---

### Post by kvarley on 2009-10-23
Thank you so much! :)

---

