---
title: "Help playing MKV video format"
date: 2009-04-07
forum: General Help
---

### Post by Wired16 on 2009-04-07
I downloaded a copy of the league of extraordinary gentlemen 1080p and there were two files in the torrent. 
1. The video file 
2. Another a file with the extension .dts
When i play the video file with any media player there is no sounds only subs.. so im thinking the dts file is subs but i want the sound to the movie. Could anyone help me?

---

### Post by mb_webguy on 2009-04-07
A dts file is actually a Digital Theater Surround audio file.  I'd say that you have separate audio and video streams.  You need to use mkvtoolnix-gui to put these into a mkv container.  I'm not sure what media player will play it, though.

EDIT:  VLC will play dts audio.  I'm not sure about any others.

EDIT:  Btw, that's not a very common mkv file.  While the matroska container can hold any type and number of audio and video streams, usually you'll find mkv's with h.264 video and AAC or AC3 audio.

---

### Post by 3Miro on 2009-04-07
For me, both mplayer and dragoon open .mkv files. You may have to explicitly select an audio track or something. I am not sure (when the sound is not working for me, it is a pulseaudio problem).

---

