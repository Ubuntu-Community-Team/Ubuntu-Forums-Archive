---
title: "VLC produces horrible sound"
date: 2006-09-10
forum: Desktop Environments
---

### Post by erusan on 2006-09-10
I'm having a problem with VLC sounding absolutely HORRIBLE when playing music files (possibly a problem with all sound, but it's harder to notice on videos).  Doesn't matter if it's mp3, ogg, flac, etc, it's just horrible.  It sounds slightly distorted, and the bass has no separation...almost as if the bass were coming through the smaller speakers as well.  Anyone else having this problem?

---

### Post by richemmanuel on 2008-01-23
Yup - I'm having this problem too. Please let me know if you find the solution. I'll keep you in touch how I get on.

Cheers
Rich

---

### Post by RawMustard on 2008-01-24
In Gutsy?

Works ok for me on one computer and is crackly/static in another :(

Always worked fine with past versions of ubuntu.

---

### Post by Skairaven on 2008-01-24
I use XMMS for all my music needs and haven't had a problem with it. If you want to use VLC then I can't help you there sorry.

---

### Post by richemmanuel on 2008-01-27
After further investigation (i.e installing mplayer and trying the same) it turns out that the problem is a constant across all video/audo playback apps, including the flash plug-in in FireFox.

The sound is squeaky and poppy, but is not evident in periods of silence. Also, if I move the mplayer window so that the video is off screen, or for whatever reason the video frame is not updating, then the interference dies down considerably.

I've downloaded and installed the most recent codecs from MPlayer, but that has had no effect, thus I suspect it is something at a lower level.

I've not figured out how to update the ALSA drivers yet (help please) to see if they are causing a problem.

I've tried 2 sound-cards (admittedly both creative/creative compatible) , both of which show the same problem. 

I deperately want to stick with K/Ubuntu if poss, but if I don't get this sorted soon I'll give up and revert to XP (which is a shame). 

Rich

---

### Post by richemmanuel on 2008-01-27
PS - Forgot to add - I have Dapper, with a few extra packages.

---

### Post by RawMustard on 2008-01-27
Are you using Gutsy 7.10?  If your computer is a bit older, try using Feisty 7.04 it had none of these problems.  Gutsy seems to bet the very worst release of Ubuntu ever :(

---

### Post by richemmanuel on 2008-01-27
Well, I'm even older than that - I'm using Dapper!

---

### Post by richemmanuel on 2008-01-28
Just to let you know I managed to fix my problem. It wasn't a software thing at all but a hardware problem. Not sure if it was a clash of interrupts or what, but moving the video card to a different PCI slot fixed the prob. I had previously tried swapping my other cards around but no luck until I actually moved the video card.

Hope this helps someone.:

Regards
Rich

---

### Post by Xgen on 2008-01-28
Please mark as 'Solved' under Thread Tools

---

