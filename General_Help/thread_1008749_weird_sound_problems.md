---
title: "weird sound problems"
date: 2008-12-11
forum: General Help
---

### Post by r0k3t on 2008-12-11
Hi there, 

I have been working through other posts but nothing has helped and my problem seems to be a little different than most. I just installed 8.10 on a dell Dimension 4600 with a built in Intel ICH5 - IEC958 sound card. 

When I log in I hear sound just fine but when I go to preferences and click test sound the box pops up but I hear nothing. I tried setting it to my card (which was in the list) however I still hear nothing. How am I hearing sound when I log in and then nothing? 

Is some process crashing? 

I am out of options as to where to look...

Thanks!

---

### Post by SmokinJuan on 2008-12-12
run
```
alsamixer
```
from a command line and unmute (press m) anything that looks important.  If that doesn't work unmute everything.

---

### Post by r0k3t on 2008-12-12
Hmm? All it shows is the master volume, how do I see other things?

Thanks

---

### Post by Ubuntist on 2008-12-12
r0k3t, have you followed the "Comprehensive Sound Solutions" sticky thread at the top of the Multimedia & Video sub-forum?  Lots of suggestions there.

---

### Post by SmokinJuan on 2008-12-12
try
```
alsamixer -c 0
```
that selects the controls for card 0.  you might also try card 1, but 0 should suffice, assuming this is your problem.

---

### Post by markbuntu on 2008-12-12
Try this:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

If that does not work for you go here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)


That "Comprehensive Sound Solutions" sticky is more of a drastic last resort sort of thing rather than a realistic basic troubleshooting guide for most people who just need a little direction to figure it out for themselves.

---

