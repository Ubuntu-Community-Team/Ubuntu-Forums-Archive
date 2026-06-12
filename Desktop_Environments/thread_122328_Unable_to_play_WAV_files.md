---
title: "Unable to play WAV files"
date: 2006-01-27
forum: Desktop Environments
---

### Post by Azguz Bloodfist on 2006-01-27
Hello,
I installed Kubuntu a couple of days ago, and have been in the process of setting everything up, firefox, flash, java etc...

 I've downloaded a whole load of packages and I'm able to play mp3 and wma files in amarok, but I'm unable to play WAV files for some reason.

Has anyone else had this problem, or is there a package/codec I'm missing?

Thanks

Eddy Seager

---

### Post by Neo Ex on 2006-01-27
Have you installed all gstreamer-* plugins?
For example, I've done a search with Adept, and I've found gstreamer0.8-audiofile. His description says:

AudioFile plugin for GStreamer

This GStreamer plugin enables the processing of audio data from formats supported by libaudiofile including AIFF, AIFF-C, **WAVE**, NeXT/Sun, BICS, and raw data.

[http://oss.sgi.com/projects/audiofile/](http://oss.sgi.com/projects/audiofile/)

I think this is the package that you are missing.

---

### Post by Azguz Bloodfist on 2006-01-27
I've got that, and I've had some success playing wave files since installing mplayer. However Amarok either crashes (with jerky playback) or refuses to play them. 

Mplayer played some wave files, one gave a "alsa-uninit: pcm closed" message, and another sounded jerky and printed lots of output like this: -

alsa-space: xrun of at least 0.007 msecs. resetting stream
alsa-space: xrun of at least 0.006 msecs. resetting stream
alsa-space: xrun of at least 0.006 msecs. resetting stream
alsa-space: xrun of at least 0.006 msecs. resetting stream
alsa-space: xrun of at least 0.007 msecs. resetting stream
alsa-space: xrun of at least 0.006 msecs. resetting stream

Very strange.

---

### Post by Neo Ex on 2006-01-27
Try running 'gst-register-0.8'. If this doesn't help, try installing amarok-xine and setting the Xine engine in amaroK preferences.

---

### Post by Azguz Bloodfist on 2006-01-28
:D Thank you very much for your help and quick responses. I did exactly as you said and now I can play wave files along with mp3 and wma :D

---

