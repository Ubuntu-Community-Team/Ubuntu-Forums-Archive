---
title: "Overlay sound in a video"
date: 2006-09-09
forum: Desktop Environments
---

### Post by cwaldbieser on 2006-09-09
I have a video file (MPEG) and an audio file (MP3) that I want to combine.  The video already has its own sound.  I don't want to eliminate the sound from the video-- I just want to play the music on top of it.

I tried using ffmpeg to do this:
```

$ ffmpeg -ac 2 -i music.mp3 -i video.mpeg out.mpeg

```
but the music from the mp3 is *replacing* the sound from the original video.

I am new to the whole video/audio editing thing, so I hope what I am describing makes sense.  Any help or pointers would be appreciated.

EDIT:
I found that I could user ffmpeg to create a second sound file from the video:
```

$ ffmpeg -i video.mpeg sound.mp3

```
I could then pull both sound files into audacity and mix them.  I can then replace the sound in the video:
```

$ ffmpeg -i mixed_sound.mp3 -i video.mpeg finished.mpeg

```
This works, but I can't help thinking that there is probably an easier way to do this sort of thing from the command line.

---

