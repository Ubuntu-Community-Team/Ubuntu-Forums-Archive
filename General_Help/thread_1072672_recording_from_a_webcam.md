---
title: "recording from a webcam"
date: 2009-02-17
forum: General Help
---

### Post by OsamaK on 2009-02-17
Hello. I want to record from my webcam, it's working well with kopete ([here is the output]("http://paste.ubuntu.com/119371/") of running kopete and viewing a preview of the webcam, which is again working well).

I tested the command as found in Ubuntu Wiki:

[I] mencoder tv:// -tv driver=v4l:width=1280:height=1024:device=/dev/video0 -ovc lavc -o webcam.avi
[/I]
and the output is [this]("http://paste.ubuntu.com/119372/"). then I tested:
*ffmpeg -vd /dev/video1 -ad /dev/dsp2 -acodec mp3 -vcodec mpeg4 -vtag xvid -s 320x240 -r 25 -y webcam.avi*
and the output is [this]("http://paste.ubuntu.com/119376/").

I think the kernel is OK with this type of webcam, but something wrong around. My webcam is 'built-in' with my Toshiba laptop.

---

### Post by RuarriS on 2009-02-17
instead of -vd try -video

---

### Post by OsamaK on 2009-02-17
*ffmpeg: unrecognized option '-video'*
nether
*ffmpeg: unrecognized option '--video'*

---

