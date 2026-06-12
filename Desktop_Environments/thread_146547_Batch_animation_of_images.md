---
title: "Batch animation of images"
date: 2006-03-18
forum: Desktop Environments
---

### Post by stalefries on 2006-03-18
I have something along the lines of a hundred images that I want to stick together in an animation. The format doesn't matter too much. i found [this Newsforge article]("http://software.newsforge.com/article.pl?sid=05/07/01/1959251&tid=131") on ImageMagick, but that means I would have to type in every single filename, which I'd rather not do. Could anyone point me to something, perhaps along the lines of some sort of GIMP plugin, or perhaps give me some handy command-line arguments to do this? If it helps, the images go in sequence from "2006-2-18 014.jpg" through "2006-2-18 160.jpg". Yes, I have heard of GIMP-GAP, and I haven't been able to find a way to use it. I am also aware of GIMP's built-in gif animation capabilities, but manually bringing in over 100 images, especially with GIMP's massive memory requirements, doesn't sound like a good use of time. Thanks in advance!

P.S.: Sorry if this is in the wrong forum, I couldn't find the art-related sub-forum after the site redesign.

---

### Post by Dragineez on 2006-03-20
Virtualdub does this. It will take a series of images and put them together into an avi file. You can even include a soundtrack if you like. Windows software, but it is FOSS. Very good and very powerful.

---

### Post by souki on 2006-03-20
you can do that with transcode and the imlist import module
search google with "transcode imlist"

---

### Post by stalefries on 2006-03-20
Thanks to both of you. I'll look into both of those. By the way, will Virtualdub run under Wine? I'm running 0.9.10, if it helps. Maybe I'll just check the Wine Appdb for it.i

---

### Post by stalefries on 2006-03-20
I've got Virtualdub running under Wine, but I don't know where to start. I've got all the files in one folder, and all I need is to stick 'em all in a row, switching from one image to the next every, oh, 200 ms. That seems fairly simple, right?

---

### Post by stalefries on 2006-03-20
I managed to figure out how to open all the files, but it then whacked out on me and used up more than the whole screen. I think I'll tell Wine to limit it to a "virtual' desktop area, and see if that works.

---

### Post by stalefries on 2006-03-25
That didn't help. Hopefully someone else has a good idea.

---

### Post by stalefries on 2006-03-29
Anyone else got an idea? I still haven't found a good solution.

---

### Post by stalefries on 2006-04-03
souki: I found this site:
[http://www.transcoding.org/cgi-bin/transcode?Import_Modules/Import_Imlist](http://www.transcoding.org/cgi-bin/transcode?Import_Modules/Import_Imlist)
and followed its directions, but not only does it seem that the file ended up in the bit bucket, the movie ended up being about 5 seconds, much less than what I want. I'd prefer something along the lines of, oh, 15 minutes? I have 146 "frames" by my calculations, so it seems that I need ~10 frames per second.

---

