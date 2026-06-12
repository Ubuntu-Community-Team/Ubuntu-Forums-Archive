---
title: "TVtime and MythTV together?"
date: 2005-12-01
forum: Desktop Environments
---

### Post by quietglow on 2005-12-01
Does anyone have both TVtime and MythTV running well on the same machine? If so did you have to do anything to get them to play nicely together?

 I have myth working perfectly, but I'm getting no lovin' from TVtime: it doesn't seem to be able to find my card. I thought it might have something to do with the running myth backend, but shutting that down did not help things out. 

I'm going to go into full blow "problem solving mode" with this, but if there is something simple that someone else knows about getting them both working on the same machine, I'd rather know about it :-)

---

### Post by quietglow on 2005-12-03
Uh, duh. the problem is that the ivtv driver, used with myth, doesnt work with tvtime. From the TVtime page:
> 
The ivtv driver supports cards that provide high quality MPEG2 encoded video. This cards are ideal for PVR systems. However, tvtime has no MPEG2 decoding capabilities or audio playback code, and therefore cannot be used to watch live TV from these cards.

RTFM, I suppose! Now I need to try to figure out what driver I might use with the card, or what sort of player supports MPEG2 playback.

---

