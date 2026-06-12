---
title: "Codecs messed up?"
date: 2009-03-13
forum: General Help
---

### Post by The Joe on 2009-03-13
Using the mplayer command to dump audio

```

mplayer -dumpaudio -dumpfile audio.mp3 video.flv
```

I am greeted with the following: 
```
[flv @ 0x8836f48]Unsupported video codec (7)
[flv @ 0x8836f48]Unsupported video codec (7)
[flv @ 0x8836f48]Unsupported video codec (7)
[flv @ 0x8836f48]Unsupported video codec (7)
[flv @ 0x8836f48]Unsupported video codec (7)
[flv @ 0x8836f48]Unsupported video codec (7)
[flv @ 0x8836f48]Unsupported video codec (7)
[flv @ 0x8836f48]Unsupported video codec (7)
[flv @ 0x8836f48]Unsupported video codec (7)
[flv @ 0x8836f48]Unsupported video codec (7)
[flv @ 0x8836f48]Unsupported video codec (7)
[flv @ 0x8836f48]Unsupported video codec (7)
[flv @ 0x8836f48]Unsupported video codec (7)
[flv @ 0x8836f48]Unsupported video codec (7)
[flv @ 0x8836f48]Unsupported video codec (7)
Core dumped ;)

Exiting... (End of file)

```

Are my codecs messed up? How can I completely remove the appropriate package and then reinstall it?

---

### Post by The Joe on 2009-03-13
A bit of a bump.

---

### Post by andrew.46 on 2009-03-13
Hi,

If you are trying to extract the audio from a flash video have you thought of using FFmpeg instead of MPlayer / MEncoder? If you are interested try running FFmpeg across one of your flv files to identify it completely:

```
ffmpeg -i video.flv
```

This is usually a good idea as the audio in flv files can vary more than a little and thus the encoding syntax can differ markedly.

All the best,

Andrew

---

### Post by The Joe on 2009-03-14
Gives the same error unfortunately, must be the codecs.

---

### Post by The Joe on 2009-03-15
Bumped my head just then.

---

