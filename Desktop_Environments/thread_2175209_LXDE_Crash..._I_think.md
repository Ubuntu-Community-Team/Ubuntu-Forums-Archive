---
title: "LXDE Crash... I think"
date: 2013-09-18
forum: Desktop Environments
---

### Post by benjjo on 2013-09-18
Hi, my desktop environment will no longer load up. I start my pc and it loads up to a blinking curser. 

Can anyone point me in the right direction, it's been so long since iv had to deal with a crash like this that I can't even remember where to start looking for fault logs etc...

I have tried ctrl+alt+F1 and running startx, but all i get is:

```
Initializing built-in extension blah blah blah
loading extension GLX
No protocol specified

waiting for X server to begin accepting connection .

No protocol specified

..
No protocol specified

..
No protocol specified

etc
```

The last thing i did was try and load up some software to my Arduino via the standard IDE software and that program hung. when i tried to log out and restart X it only gave me a blinking curser. So i tried ctrl+alt+F1 and ran shutdown. 

Any ideas? Direction??

Cheers, sorry if this is in the wrong thread, im not really sure what kind of problem this relates to.

---

### Post by benjjo on 2013-09-18
OMG!

OK, this takes the cake for the all time no0b award. I just ran a df -h and yep, you guessed it, i ran out of space!

sorry for wasting your time guys. 

My only excuse is, i got so caught up in trying to remember which log file was where that i over looked the simple stuff. I also forgot about a program that was running in the background writing to it's own log file ( 17GB log file ). 

What can i say, it's been a long day :(

---

