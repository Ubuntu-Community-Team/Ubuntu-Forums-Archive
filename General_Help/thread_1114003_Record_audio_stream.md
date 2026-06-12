---
title: "Record audio stream"
date: 2009-04-02
forum: General Help
---

### Post by matemargo on 2009-04-02
Hi, I use to listen an Internet radio using Rythmbox. I wanted to record the streaming using this command:

```

ffmpeg -i http://streaming.fmrockandpop.com/rockandpop -ab 128 -ar 44100 rockandpop.mp3

```

But I get this error
```

http://streaming.fmrockandpop.com/rockandpop: Unknown format

```

Should I use another command or different parameters?

Thanks.

---

### Post by Cybie257 on 2009-04-02
From what I understand, Audicity and VLC are capable of recoding streaming audio. Maybe that would work better/easier instead of command line options???

-Cybie

---

### Post by ajgreeny on 2009-04-02
It is perhaps also worth looking at **streamripper** which can rip streams to mp3 very easily, though it does depend on what type of stream is coming downstream.  I use it quite often with cron to time a recording of various radio broadcasts.  For that, in order to make things easier, I use bash script files which are executed with cron; job done!

---

### Post by andrew.46 on 2009-04-02
Hi matemargo,

> **matemargo said:**
> I wanted to record the streaming using this command:
```

ffmpeg -i http://streaming.fmrockandpop.com/rockandpop -ab 128 -ar 44100 rockandpop.mp3

```

But I get this error
```

http://streaming.fmrockandpop.com/rockandpop: Unknown format

```


This appears to be an asf stream which perhaps FFmpeg has trouble with. Your syntax works on other streams, for example my favourite radio station:

```
ffmpeg -i http://www.abc.net.au/streaming/classic/classicfm.m3u -ab 128 -ar 44100 test.mp3
```

I will admit to being unaware that FFmpeg could actually capture streams in this manner :-). However MPlayer *will* capture your stream and save as pcm:

```

mplayer -cache 1024 http://streaming.fmrockandpop.com/rockandpop \
        -vo null -vc null -ao pcm:fast:waveheader:file=rockandpop.wav

```

Then convert with lame or FFmpeg as you wish.

All the best,

Andrew

---

