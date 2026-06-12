---
title: "Getting totem-xine or gxine to play streams"
date: 2006-07-06
forum: Desktop Environments
---

### Post by hajk on 2006-07-06
Totem-xine or Gxine won't play streaming audio/video directly, complaining about the source (like [http://www.cbc.ca/clips/national/thenational.ram](http://www.cbc.ca/clips/national/thenational.ram)) being an empty file.

Yet, I can use "wget" with such an address, which makes a file "thenational.ram" in my home directory, containing a single line with a redirection  address, in the example it is rtsp://a420.v87525.c8752.g.vr.akamaistream.net/ondemand/7/420/8752/1152154260000/origin.media.cbc.ca/clips/national/thenational.rm.
When I point totem-xine (or gxine) to this file it plays fine.

I'm wondering why totem-xine or gxine don't follow redirections -- is there something to configure to make them do it?

---

### Post by H.E. Pennypacker on 2006-07-08
I am using Totem-Xine and Gxine, and I am not having any problems.  I copied and pasted the URL you gave into the Firefox bar, and and it opened up Totem-Xine.  I can't even believe the quality...its great!  It hasn't buffered either!

---

### Post by hajk on 2006-07-08
Yes, Firefox takes care of the address redirection -- there are several intermediate links, finally ending in an rtsp://... address that changes every weekday. Using wget also follows the links and prints the final address in a file. My question was why totem-xine or gxine *themselves* don't follow the links: without that feature, the original address won't work in the favourites/media of the player.

---

### Post by H.E. Pennypacker on 2006-07-08
This is a problem you are facing, because this time, I simply clicked on the URL, and it opened in Totem-Xine.  I didn't copy and paste the URL.  After clicking on the URL, Firefox asked what to open it with.  I chose Totem.  It then played.

That's all.  Change everything to default to make sure you haven't done anything wrong.

---

