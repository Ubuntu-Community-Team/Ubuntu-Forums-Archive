---
title: "How do I strip soundtrack from video?"
date: 2009-02-08
forum: General Help
---

### Post by t0p on 2009-02-08
I've got a youtube-type video file (.flv) from which I want to strip and  save the soundtrack. How do I go about doing that?

---

### Post by amauk on 2009-02-08
using ffmpeg is probably the easiest

```
ffmpeg -i ./youtube-vid.flv ./audio-only.mp3
```

---

### Post by FakeOutdoorsman on 2009-02-08
Yes, FFmpeg is definately the way to go.  If you don't know the audio format you can use FFmpeg to tell you what it is:
```
ffmpeg -i input.flv
```
The output will include something like the following:
```
Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 56 kb/s
```
Now that I know it is mp3 audio, I can just copy the audio stream.  There is no re-encoding, so the quality is preserved:
```
ffmpeg -i input.flv -acodec copy -vn output.mp3
```
The "-vn" option tells FFmpeg to ignore the video.  It isn't required for audio only formats such as mp3, but you would have to use it for containers such as ogg or mp4 that can contain both video and audio streams.

If you want to encode from one format to another that is restricted (such mp3, aac etc), you will need to install the **libavcodec-unstripped-51** package to enable these restricted encoders in FFmpeg.  I don't think you will need this package to copy the stream like the example above.

---

### Post by t0p on 2009-02-09
Thanks people!

---

