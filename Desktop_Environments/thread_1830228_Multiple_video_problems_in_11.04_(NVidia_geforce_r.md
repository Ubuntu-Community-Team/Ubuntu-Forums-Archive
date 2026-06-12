---
title: "Multiple video problems in 11.04 (NVidia geforce related, perhaps)"
date: 2011-08-21
forum: Desktop Environments
---

### Post by brel on 2011-08-21
I've had a lot of problems with 11.04 and I've sort of assumed they were being worked on and things would get better. They are not. It's been almost four months since 11.04 came out and Unity feels as rough around the edges as it was in the beginning. I'm really not sure what to do.

Here are my problems:
  * EVERY time I get back from suspend, my screen is scrambled and I'm forced to do a 'compiz --replace'. Shouldn't ubuntu do this automatically?
  * Occasionally, after my 'compiz --replace' the unity bar at the right leaves a black strip under it that blocks everything under it.
  * Video: my video playback keeps getting stuck on a frame. Audio continues and after about ten or fifteen seconds the video comes back. I've tried VLC, mplayer and xine. Same problem in each one.

A while back I downgraded to nvidia driver 173 (see [this thread]("http://ubuntuforums.org/showthread.php?t=1746945")) because of blank screen issues. Since my problems seem video related, I recently tried upgrading to the latest nvidia driver (275.21, I've a geforce 7025). The blank screen issue mentioned in the thread is STILL an issue!!!

So what are my options?
  * Hope that ubuntu upgrades fix things?
  * Hope that nvidia fixes things?
  * Give up on unity?
  * Upgrade my graphics?

I'm really frustrated. I've never had such a shoddy linux system (well maybe kde 4.0 was comparable). Are any of these issues being worked on or should I cut my losses???

Thanks.

(it might be relevant that my installed system is xubuntu and I installed unity later)

---

### Post by brel on 2011-08-22
My problems are solved. It was all down to the video driver. I upgraded to the latest (280.21 I think), fixed my frame buffer size (in the bios I upped it from 64 to 256) and now everything works.

I'm not sure how old my other driver was (it was v173) but it shouldn't be the root of all these problems.

I'm going to avoid nvidia in the future.

---

