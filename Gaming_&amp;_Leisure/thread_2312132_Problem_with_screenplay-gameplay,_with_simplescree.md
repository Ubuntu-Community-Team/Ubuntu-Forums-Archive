---
title: "Problem with screenplay-gameplay, with simplescreenrecorder."
date: 2016-02-02
forum: Gaming &amp; Leisure
---

### Post by Portaro on 2016-02-02
Hello, 

I have a problem when I try to record a gameplay, in the game I dont have any lag or any problem but when I finish gameplay and save the video the result is like this -

[https://youtu.be/CTNt-KnlnBE](https://youtu.be/CTNt-KnlnBE)

My question is -

Why the video have this problem and what can cause this?

Thanks.

---

### Post by potato5 on 2016-02-02
Slow performance of your computer.
 Try ffmpeg (I do not know what's captured video before).

> 
Lossless recording

If you want a perfect recording of your desktop, x264 can help. Use lossless encoding, e.g.:

ffmpeg -video_size 1920x1080 -framerate 30 -f x11grab -i :0.0 -c:v libx264 -qp 0 -preset ultrafast capture.mkv

-qp 0 tells x264 to encode in lossless mode, -preset ultrafast advises it to do so fast.

The encoder should be fast enough on most modern hardware to record without any framedrop, and even leave enough CPU headroom for other applications.

If you're going to archive the recording or are concerned about file size, re-encode it losslessly again but with a slower preset. Note that since the initial recording was lossless, and the re-encode is lossless too, no quality loss is introduced in this process in any way.

ffmpeg -i capture.mkv -c:v libx264 -qp 0 -preset veryslow capture_smaller.mkv

[https://trac.ffmpeg.org/wiki/Capture/Desktop#Losslessrecording](https://trac.ffmpeg.org/wiki/Capture/Desktop#Losslessrecording)

---

### Post by Portaro on 2016-02-02
:D Thanks , I take a look now on ffmpeg. Maybe can work, thanks.

---

