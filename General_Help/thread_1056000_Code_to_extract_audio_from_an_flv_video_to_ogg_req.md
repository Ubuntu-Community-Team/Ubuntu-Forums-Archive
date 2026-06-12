---
title: "Code to extract audio from an flv video to ogg required"
date: 2009-01-31
forum: General Help
---

### Post by Rytron on 2009-01-31
Hi.
I came across this ace code on another thread.
```
mplayer -dumpaudio videohere.flv -dumpfile nameofoutput.mp3
```
Is there a way to modify the above code so that the output file is .ogg?

---

### Post by cafeytv97 on 2009-02-01
I only know how to do that with ffmpeg

```
ffmpeg -i video.flv -vn -acodec vorbis -ac 2 -ar 44100 -ab 128k  audio.ogg
```

-i: input file
-vn: no video
-acodec: audio codec
-ac: audio channels
-ar:audio sampling rate
-ab: audio bitrate

---

### Post by Rytron on 2009-02-01
> **cafeytv97 said:**
> I only know how to do that with ffmpeg

```
ffmpeg -i video.flv -vn -acodec vorbis -ac 2 -ar 44100 -ab 128k  audio.ogg
```

-i: input file
-vn: no video
-acodec: audio codec
-ac: audio channels
-ar:audio sampling rate
-ab: audio bitrate

ffmpeg will do fine. Thank you cafeytv97. Your code works perfectly.

---

### Post by Rytron on 2009-04-17
> **cafeytv97 said:**
> I only know how to do that with ffmpeg

```
ffmpeg -i video.flv -vn -acodec vorbis -ac 2 -ar 44100 -ab 128k  audio.ogg
```

-i: input file
-vn: no video
-acodec: audio codec
-ac: audio channels
-ar:audio sampling rate
-ab: audio bitrate

To extract audio at a higher bit rate, would I just use this:
ffmpeg -i video.flv -vn -acodec vorbis -ac 2 -ar 44100 -ab **192k**  audio.ogg

Or do I need to change more values?

---

### Post by FakeOutdoorsman on 2009-04-17
Yes, that should do it:
```
ffmpeg -i video.flv -vn -acodec vorbis -ab 192k audio.ogg
```
I omitted some of the options because you probably don't need to force a sample rate or make it stereo if the input is mono only.

---

### Post by Rytron on 2009-04-19
> **FakeOutdoorsman said:**
> Yes, that should do it:
```
ffmpeg -i video.flv -vn -acodec vorbis -ab 192k audio.ogg
```
I omitted some of the options because you probably don't need to force a sample rate or make it stereo if the input is mono only.

Thank you FakeOutdoorsman. Cheers.

:popcorn:

---

