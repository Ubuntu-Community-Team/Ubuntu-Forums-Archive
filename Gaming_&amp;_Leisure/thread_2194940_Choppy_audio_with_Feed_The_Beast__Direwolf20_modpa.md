---
title: "Choppy audio with Feed The Beast / Direwolf20 modpack"
date: 2013-12-21
forum: Gaming &amp; Leisure
---

### Post by salimfadhley on 2013-12-21
The audio is choppy (stuttering) on my Dell XPS 13 Developer Edition laptop. It sounds like all sounds are punctuated by short gaps of silence at about 2-3hz. It makes the game unplayable with the volume on.

Oddly enough, it plays fine on all my old desktop PCs. It only produces this annoying effect on my laptop. 

I've tried using Open JDK versions 6 and 7. I've used Oracle JRE 7. I'm launching the game via the FtB launcher and using the very latest Direwolf20 modpack.

Can anybody offer some advice about how I might resolve this situation?

Sal

---

### Post by oldrocker99 on 2013-12-21
Try this:

killall pulseaudio

Sometimes, it works.

---

### Post by oldrocker99 on 2013-12-21
Try this:

killall pulseaudio

Sometimes, it works.

---

### Post by salimfadhley on 2013-12-21
Actually I just discovered the cause of the problem: I was using "Analogue Stereo Duplex" output mode rather than "Analogue Stereo". Flipping the output in PAVC fixed the issue.

---

