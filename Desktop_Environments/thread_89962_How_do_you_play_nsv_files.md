---
title: "How do you play nsv files?"
date: 2005-11-13
forum: Desktop Environments
---

### Post by mog27 on 2005-11-13
I have spent forever trying to figure out how to successfuly play nsv streams (nullsoft video streams) in mplayer, vlc player and about any other darn player I could think of.  I have even asked on other boards and no one has come up with a working solution.  mplayer should be able to play it but I get an error of "Couldn't resolve name for AF_INET6:ip address" (ip address is the ip address of stream). I am using the following syntax with mplayer:

mplayer [http://username:login@ip_address:_port/stream.nsv](http://username:login@ip_address:_port/stream.nsv) (I had to put an underscore before the 'p' on this post because a colon and a 'p' together produces a smiley face)

username and login is the l/p to get into the stream.  Gold star to whoever knows a solution or can figure out what's wrong because I have been forever trying to figure it out and google and README files provide no help.

---

### Post by oskude on 2005-11-14
i can play the streams at [www.demoscene.tv](www.demoscene.tv) (they use nsv) with mplayer and w32codecs...

as it says: "Couldn't resolve name for AF_INET6:ip address" your problems is with network, not nsv video...

---

