---
title: "audio and video problems"
date: 2006-09-22
forum: Desktop Environments
---

### Post by jimonade on 2006-09-22
hello ubuntu forums!

i have 2 problems.

1) when listening to audio using xmms or rhythmbox, after several hours of continuous playback of a mix of mp3/ogg, the sound starts skipping.  the skip repeats a ~.5 sec segment of the current file ~10 times, then moves on to the next ~.5 sec segment.  it continues to do this until interfered with.  closing the app fixes it after a ~30 sec delay.  i usually just kill-9 and start again.  i listen to music while i sleep at night, and have woken up 6 hours in to this problem.  i thought at first it may be related to hdparm and disk spin-downs, but i have set my ide hd's to spin down after 2 hours.  i dont use sleep or hibernate modes.  the problem exists on 2 different desktop pc's in my household (1 amd custom built, 1 intel dell).  the amd box was running gentoo 5 months ago and never had this problem.  

2) when viewing video in totem, realplayer, or flash-player-plugin (in firefox) the video will occasionally stall for up to 10 seconds.  the fact that it happens in totem/real/flash is a big clue here, but i dont know what it means.  different formats, different resolutions, different codecs... doesnt seem to matter.

maybe these 2 problems are related, maybe not.  im sadistically hoping that others here have had this problem so i will get some juicy solution feedback.

if i can post any additional sys info to help track this down please let me know.

i evangalize linux often, and hate when these problems show up during an ubuntu gnu/linux show-off session.

thanks in advance,

-j

---

### Post by hansel_nz on 2006-09-30
I can also report the second problem in Dapper. 

All audio players frequently pause (for about 5 seconds) and I get a similar thing when watching video. It's not debilitating because it doesn't happen that frequently. Usually occurs about twice when I'm watching a full length movie.

It affects all movie/audio players so it is obviously something fundamental. It only started occuring after I upgraded to dapper.

Would be very interested in identifying the problem.

Cheers 

Hansel 
Auckland, New Zealand

---

### Post by jimonade on 2006-12-07
speaking of the ~5 sec pauses...

i confirm this happening in edgy eft 6.10 also.

specifically when using amarok (xine engine)

maybe the problem is tied to xine in some way.  i use totem-xine instead of totem-gstreamer.

-j

---

