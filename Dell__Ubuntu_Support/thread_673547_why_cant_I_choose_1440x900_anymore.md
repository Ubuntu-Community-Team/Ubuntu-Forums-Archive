---
title: "why cant I choose 1440x900 anymore?"
date: 2008-01-20
forum: Dell  Ubuntu Support
---

### Post by gruss on 2008-01-20
Everything was fine, until I decided I wanted to turn on the desktop effects, but hen wouldnt play videos, so I turned them off now I'm stuck in 1280X800 resolution when the monitor shoudl be 1440x900.  Everything looks all "blocky"  Anyway how on earth to i get to choose 1440.900 again???  It's listed in the xorg.conf file but doesnt show up in "screens and graphics".  what am I missing?
dell latitude d630 integrated intel video.

---

### Post by crispy_420 on 2008-01-20
Try a commandline reconfigure of xorg. Sorry don't remember the exact command now. It is something like "sudo dpkg reconfigure...".

---

### Post by gruss on 2008-01-20
Really odd, tried changing drivers and that was no good, had to replace the xorg with a previous one to get back...but they all seem to list 1440x900 somewhere in there but yet I cant choose it, and that seems to be the only setting where text looks ok.  kinda frustrating

I'm still curious about this, but i messed around with it a little, dont remember what I did and the text looks ok again in 1280x800, and I can live with that resolution, something just seems a little flaky.  This the kind of issue that you just hope and pray Intel updates the driver? (which I'm sure they are diligently working on ;) )  or was it my incessant need to tweak that screwed things up?

---

