---
title: "Poor video performance with ati 4250"
date: 2012-07-28
forum: Desktop Environments
---

### Post by vikktor91 on 2012-07-28
I have Ubuntu 12.04 + integrated ati 4250 + the proprietary driver.I know that the video card is not the best, but in windows it performs much better.In Ubuntu i can watch only 480p video with some tearing.With the OSS driver is even worse.When i try to type, the letters appears with some delay and everyrhing is realy slow.

Here is the result from fgl_glxgears
133 frames in 5.0 seconds = 26.600 FPS

and here from glxgears
224 frames in 5.0 seconds = 44.583 FPS

The output from glxinfo says : direct rendering: Yes

The question is, is there some kind of optimization or something else to improve my graphics performance?Thanks in advance :)

---

### Post by Jakin on 2012-07-28
I work on 880g chipset, mobile radeon 4250, set all possible max quality in CCC and not having a single issue with any playback of formats and their resolution.. or opengl desktop effects (kde plasma here) I dont play anything in 1080p though, considering the display resolution isn't that high, so why play above 720p; but there no issues with my setup.

---

### Post by vikktor91 on 2012-07-28
I'm too on 880g, and everything is in max performance in CCC.For me KDE works better than Unity and GS, but still lags sometimes, and cant play 720p or 1080p videos.On windows this video card can run Blu-ray movies without a problem.

---

### Post by Jakin on 2012-07-29
On KDE i might say try xrender instead openGL composition; see if it helps take some load off gpu to improve its performance with video.
I also have Fluendo codecs installed. and give this a shot, if you haven't already apt:kubuntu-restricted-extras?section=universe?section=multiverse
You could also try the xorg-edgers ppa, for other versions of AMD/Ati fglrx drivers (i have never myself)

---

