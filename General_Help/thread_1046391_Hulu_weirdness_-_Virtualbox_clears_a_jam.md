---
title: "Hulu weirdness - Virtualbox clears a jam"
date: 2009-01-21
forum: General Help
---

### Post by dwasifar on 2009-01-21
I'm posting this in General rather than Multimedia/Video because I think it touches on a more general issue.

I'm running 64-bit Intrepid.  When I start a Hulu video in Firefox, it just hangs; the player window comes up but the video doesn't start.  BUT, I have discovered that if I then open a Hulu video in XP inside Virtualbox, the first Hulu video in the Ubuntu Firefox window will start a few seconds later.  It does not need to be the same video.  I can then stop the XP playback, or even close the VM entirely, and the Ubuntu Firefox Hulu video will continue to play normally.

I hypothesize that the Ubuntu Firefox instance is having trouble establishing communication with the Hulu server, but the XP instance is not; and once the XP/Virtualbox instance has established communication between Hulu and my ip, both instances can talk to Hulu's servers.  But I'm not sure how I would go about testing this hypothesis or solving the problem.

---

### Post by newswitch on 2009-01-22
I have a similar problem.  I'm running 64 bit Intrepid.  Youtube and most flash videos work quickly.  However, Hulu video hangs in firefox 3 for a minute or two, and then runs fine.

Hulu video runs well in my Windows XP partition, though.

What makes Hulu video different from Youtube and flash?

---

