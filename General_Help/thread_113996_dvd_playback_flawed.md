---
title: "dvd playback flawed"
date: 2006-01-07
forum: General Help
---

### Post by Nikusan on 2006-01-07
I hope there is a fix for what I'm about to describe, but it seems like an inherent flaw in libdvdcss or something related.

When playing back DVDs I sometimes get distortion where there is sudden movement. The distortion is hard to describe so I've attached a screenshot, the screenshot is somewhere inbetween two frames, so it's not an exact deption of what I'm seeing but you should be able to gather.

That screenshot is taken from the first episode on the Family Guy "Happy Freakin' Christmas" DVD. The distortion is so bad that it makes it unwatchable. Oddly, the second episode plays perfectly.

I get similar artifacts on some futurama dvds. Perhaps it's an illusion caused by the nature of the animation (high contrast or whatever), but I only seem to have this problem with cartoons.
DMA is enabled on the drive.
I get the same problem in totem, xine, mplayer, vlc and ogle.
I've tried every combination of deinterlacing and aspect ratios, etc in the above metioned apps.

Is there something I'm missing? Hopefully this is just a problem specific to me...

---

### Post by schilcha on 2006-01-07
Good news: I know what this is... it's an interlaced video. This means, every frame contains only half of the image (as usual for tv-material). One frame has the even lines, the other has the odd lines.

Bad news: I don't know how to get rid of it... What you need is a de-interlacer. A filter that blurs the successive half-images into each other. I've no idea how to do this with the movie-players. At least, mplayer-man-pages says something about deinterlacing (see "man mplayer" and search for deinterlace).

Good Luck!

---

