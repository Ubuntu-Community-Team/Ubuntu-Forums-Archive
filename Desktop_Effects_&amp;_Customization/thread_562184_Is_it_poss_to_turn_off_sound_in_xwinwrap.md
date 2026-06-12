---
title: "Is it poss to turn off sound in xwinwrap?"
date: 2007-09-28
forum: Desktop Effects &amp; Customization
---

### Post by Uber Nooblett on 2007-09-28
hey, I've been playing around with xwinwrap today and cant seem to figure how to switch off the sound when I'm using it to play a movie as the desktop... is there a way of doing this?

I'd really like to have the movie playing as desktop and continue to listen to other things (music etc) with the movie on silent and just there to look pretty.

Any help appreciated

JJ

current startup code =

```
xwinwrap -ni -fs -s -st -sp -b -nf -- mplayer -wid WID -quiet ************.avi
```

---

### Post by Uber Nooblett on 2007-09-28
nvm :D 

I just added '-nosound' in there after  '-quiet' and HEY PRESTO :D

---

