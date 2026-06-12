---
title: "Totem video playback issue"
date: 2005-11-08
forum: Desktop Environments
---

### Post by jaddison on 2005-11-08
I've got a few videos that seem to sort of 'lock up' partway through playback. I say 'sort of' because the audio keeps playing fine, while the video stream looks as though it's paused!

Has anyone else noticed this issue?  I am using xine as the backend.

Thanks,

---

### Post by tmadsen on 2005-11-08
sudo apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg w32codecs

That did everything for me... otherwise vlc plays almost everything too.

---

### Post by jaddison on 2005-11-09
[QUOTE=tmadsen]sudo apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg w32codecs[/QUOTE]

Oh, I've got all that jazz already - and it didn't work very well when I was gstreamer based.  Any other suggestions?

Thanks though!

---

