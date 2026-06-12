---
title: "Linux equivalent for TotalRecord"
date: 2005-11-05
forum: Desktop Environments
---

### Post by Joe_lurker on 2005-11-05
I use a program on Windows called TotalRecord.  It is an audio stream recorded that can basically record any audio.  It sets up a driver and inturcepts the audio stream.  It also allows you to record as fast as the stream arrives.  I can get an hour show in about 20 minutes.  I usually use it to record Real streams from the internet but I have used it to record the audio from Flash animations.

Does anyone know of any similar tools on Linux?  I can use MPlayer to rip Real audio streams but I would imagine that there are some other programs out there.  I also need to encode them to mp3 for myPod.

With the open nature of the sound system on Linux I would imagine that tools like this would be available.

Thanks,
Joe

---

### Post by Iandefor on 2005-11-05
You can use Audacity to record the audio out stream, but I think it'll only record in real-time; However, it will export to mp3 if you have LAME (LAME ain't an MP3 encoder). To get them, make sure you have the Uni/Multiverse repositories enabled and enter the following into a terminal: ```
sudo aptitude install audacity lame
```

EDIT: I realised that the command I suggested was incorrect insofar that in order to install both Audacity and LAME, you need to pass the argument 'install' on the command; I corrected it

---

### Post by matthew on 2005-11-05
```
sudo apt-get install aptitude audacity lame
```

---

### Post by trigg on 2005-11-05
[QUOTE=Joe_lurker]I use a program on Windows called TotalRecord.  It is an audio stream recorded that can basically record any audio.  It sets up a driver and inturcepts the audio stream.  It also allows you to record as fast as the stream arrives.  I can get an hour show in about 20 minutes.  I usually use it to record Real streams from the internet but I have used it to record the audio from Flash animations.

Does anyone know of any similar tools on Linux?  I can use MPlayer to rip Real audio streams but I would imagine that there are some other programs out there.  I also need to encode them to mp3 for myPod.

With the open nature of the sound system on Linux I would imagine that tools like this would be available.

Thanks,
Joe[/QUOTE]


There are quite a few ways to record Real streams (and other streams - .asx, .wmv, .wma, etc) -  but the best luck I have had is by using MPlayer.  You'll have to install the w32 codecs as this thread describes:

[Restricted Formats WIki Article]("https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Codecs")

then use mplayer from the command line (this example records an NPR stream)

```

mplayer rtsp://real.npr.na-central.speedera.net:80/real.npr.na-central/fa/20051104_fa_01.rm -vo null -ao PCM:file=freshair.wav

```

"-vo null" just keeps mplayer from looking for video
"-ao PCM:file=" records a standard WAV format file.  You can probably dump it directly to MP3 or ogg, but I haven't tried - especially since I know how to control the settings with either lame or oggenc - but you could always read up on the mplayer/mencoder documentation and see what your options are. . .

Then I just recode it:

```

lame --preset standard freshair.wav freshair.mp3

```


EDIT: You could also use VLC - it even has a wizard that will walk you through it, but I haven't had much luck with it.

---

### Post by Joe_lurker on 2005-11-05
I use MPlayer now.  However the streams I want are in a playlist.  For some reason MPlayer records over the file for each stream in the playlist.  For example if the playlist has 10 streams then I get one file with the last stream, but all streams have been received.  I believe that I used to be able to do this just fine long ago but I was spoiled with TotalRecord.

BTW it's Car Talk I am trying to rip:
```
mplayer -vc dummy -vo null -ao pcm:file=cartalk.wav -playlist http://play.rbn.com/?url=cartalk/cartalk/demand/CT0545-01.ra?url=cartalk/cartalk/demand/CT0545-02.ra?url=cartalk/cartalk/demand/CT0545-03.ra?url=cartalk/cartalk/demand/CT0545-04.ra?url=cartalk/cartalk/demand/CT0545-05.ra?url=cartalk/cartalk/demand/CT0545-06.ra?url=cartalk/cartalk/demand/CT0545-07.ra?url=cartalk/cartalk/demand/CT0545-08.ra?url=cartalk/cartalk/demand/CT0545-09.ra?url=cartalk/cartalk/demand/CT0545-10.ra
```
Also using -vo null and -vc dummy should pull the stream as fast as it can be downloaded - hour show in 20 minutes.  This isn't working.  Any suggestions?

Is there a way to encode an mp3 from a Real Audio stream directly?  Then I could pipe right through.

-Joe

---

### Post by poptones on 2005-11-05
mplayer -noframedrop -dumpstream -dumpfile saved.rm rtsp://url/to/file.rm

---

### Post by Edward The Bonobo on 2006-04-19
This excellent article: [http://www.linux-magazine.com/issue/57/Ripping_Audio_Streams.pdf](http://www.linux-magazine.com/issue/57/Ripping_Audio_Streams.pdf) tells you how to do it with a combination of Vsound/Sox and Lame.  It works great!  

Note that NPR nest their stream URLs in .smil files - but you can pek inside with a text editor.

Check out the live concerts on 'All Songs Considered'


I'm having problems installing Audacity, though, due to missing dependencies.  Any ideas?

---

