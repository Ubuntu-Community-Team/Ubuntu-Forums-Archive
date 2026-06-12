---
title: "MPlayer + Xgl: what video output should I use?"
date: 2006-09-11
forum: Desktop Environments
---

### Post by kwalo on 2006-09-11
Hello!

I've set up Xgl on nvidia card and compiled MPlayer from cvs. They work fine, however I use vo=xv for MPlayer. It's fast enough, but doesn't look well (OSD subtitles are scaled with the movie). I'd  like to use other video output for MPlayer, that could place subtitles beneath movie, for better movie appearance (vo=gl, or vo=sdl can do it without Xgl). vo=x11 doesn't scale subtitles, but subtitles are shown on movie.

So far xv, gl2 and x11 work well for me. vo=gl doesn't display OSD. sdl is slow and it scales OSD subtitles (normally it shouldn't).

Is there any other video output that could work better with MPlayer and Xgl with nvidia card?

---

