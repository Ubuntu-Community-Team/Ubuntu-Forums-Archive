---
title: "HELP! Sluggish video playback when using Compiz"
date: 2007-09-27
forum: Desktop Effects &amp; Customization
---

### Post by Angellis_ater on 2007-09-27
I have just updated to Gutsy Gibbon (7.10) and activated the Compix Fusion Desktop handler - everything works fine EXCEPT for Video Playback which is sluggish, it sometimes skips a second here and there or is trudging along very labourously.

The worst effect comes when I fullscreen it, at which point you can SEE the visual updates at times as it flows down the screen.

Any help would be appreciated!

---

### Post by GepettoBR on 2007-09-27
framedrops like that usually happen when you don't have enough CPU cycles for the decoding, for instance when you have too many apps open or try running a high-res/high-br video on a slower machine. This is especially true if you're playing MPEG-4 ASP and MPEG-4 AVC compressed videos (like DivX, XviD, x.264 and Snow) since they have very complex decoding algorythms.

Maybe you should deactivate the eye-candy when playing videos. You won't see it through the fullscreen anyways.:)

---

### Post by Angellis_ater on 2007-09-27
What I don't get is what kind of CPU cycles is Compiz using when I have something in fullscreen? It doesn't need to decorate anything, no need to draw anything at all.

Is there some automatic way to disable Compiz when I use VLC for example?

---

### Post by gyrfalcon on 2008-01-03
If anyone has some additional input into this question it would be appreciated.

I'm using VLC/Movie Player/MPlayer to play x.264 1080p videos and it's skipping as well.

Generally I would think a Pentium D 930 3.0GHz dual core chip with 2gigs of RAM would stand up well to playing back this sort of video.

---

### Post by hyperair on 2008-01-03
The problem here is not the CPU power or RAM. It's video acceleration. XV doesn't work very well when Compiz Fusion is running. You could try changing the video output of all the players you use to xshm, gl, gl2, or if you're using nVidia, use XVideo with the Video Blitter.

---

