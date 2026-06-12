---
title: "Auido/Video Sync"
date: 2005-09-14
forum: Desktop Environments
---

### Post by chris86wm on 2005-09-14
When I go to watch any type of video file on my computer, it plays well at first, but about ten minutes later the audio and video dont seem to match up. I can pause the movie then play it to get it back to normal but ten minutes later its messed up. I have istalled all the codecs using this guid [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs) 
I have also tried totem and xine for playing the movies without anything running in the background. My specs are AMD 64 3200+ and a gig of ram. (I run the intel version of ubuntu do to some probs with amd) 
Am i doing something wrong?
AND
Is there an all in one player that i could use like divx that would work?
also i have crossover office if that helps with finding programs.
thanks everybody

---

### Post by WillCooke on 2005-09-15
[QUOTE=chris86wm]When I go to watch any type of video file on my computer, it plays well at first, but about ten minutes later the audio and video dont seem to match up. I can pause the movie then play it to get it back to normal but ten minutes later its messed up. I have istalled all the codecs using this guid [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs) 
I have also tried totem and xine for playing the movies without anything running in the background. My specs are AMD 64 3200+ and a gig of ram. (I run the intel version of ubuntu do to some probs with amd) 
Am i doing something wrong?
AND
Is there an all in one player that i could use like divx that would work?
also i have crossover office if that helps with finding programs.
thanks everybody[/QUOTE]
 If you're using mplayer to play your files try adding "-ao alsa" to the end of the command.

If you're not using mplayer, give it a go.

Your computer is easily up to spec to play MPEG4 fileswith out problems.

---

