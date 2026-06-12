---
title: "gstreamer cache"
date: 2006-08-24
forum: Desktop Environments
---

### Post by petersok on 2006-08-24
I would like to use rhythmbox (with gstreamer backend) to play my music library. However, there seems to be a problem.

My library is stored on a network server, and in the past, when using mplayer to play music, I have had to specify a small cache to ensure that the music does not skip because of speed limitations.  I have initiated mplayer like so:

mplayer -cache 5000 ...

Is there anyway to force gstreamer to cache a bit of my music before it starts to play when I choose a song in rhythmbox? Thanks in advance for any help...

KP

---

### Post by michux on 2006-08-24
> **petersok said:**
> I would like to use rhythmbox (with gstreamer backend) to play my music library. However, there seems to be a problem.

My library is stored on a network server, and in the past, when using mplayer to play music, I have had to specify a small cache to ensure that the music does not skip because of speed limitations.  I have initiated mplayer like so:

mplayer -cache 5000 ...

Is there anyway to force gstreamer to cache a bit of my music before it starts to play when I choose a song in rhythmbox? Thanks in advance for any help...

KP

It's not exacly what you're asking for but you can take a look at this: [http://www.ensi-bourges.fr/perso/jfl/doku.php?id=system:nas](http://www.ensi-bourges.fr/perso/jfl/doku.php?id=system:nas)

---

