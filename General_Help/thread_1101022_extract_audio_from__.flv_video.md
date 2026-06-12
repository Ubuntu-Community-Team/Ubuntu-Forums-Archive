---
title: "extract audio from  .flv video"
date: 2009-03-19
forum: General Help
---

### Post by ihatetryingtopickaloginna on 2009-03-19
Is there a way to save the audio from youtube downloads separate from the video?

---

### Post by lensman3 on 2009-03-19
There is a pearl script called "youtube-dl" that I have that will download a youtube movie and save it to your hard drive.  

Use mplayer to strip the sound:

"mplayer -dumpaudio nodame_theme.flv -dumpfile nodame_theme.mp3"

I've done it with a video and wanted the song.  Works fine.

---

### Post by ihatetryingtopickaloginna on 2009-03-20
Ok, thanks. That's what I was looking for.

---

### Post by ihatetryingtopickaloginna on 2009-03-20
Just tried it and it works great. Thanks again.

---

### Post by mb_webguy on 2009-03-20
While that's basically the way I'd do it (though I'd likely use the Video DownloadHelper extension in Firefox to download and possibly convert the video to something more usable), you can also strip the audio using VLC.  

Open VLC and go to Media->Convert/Save.  Open the file you want to strip and click Convert/Save.  At the top, check the File output, and provide a filename and location.  Choose your Encapsulation preference, make sure nothing is selected on the Video tab, check the Audio box on the Audio tab and choose the settings, and click Save.

It's not as quick as typing in that one command in the terminal, but it doesn't involve typing a command in the terminal, which scares some people who are used to doing everything with a GUI.

---

### Post by ihatetryingtopickaloginna on 2009-03-21
Another way to do it, thanks. I'm not scared of the command line, I grew up memorizing long commands and typing them in. And then batch files so I wouldn't have to type so much. When I switched from dos to OS/2 I still used the command line as much as I could.

---

### Post by Dr Small on 2009-03-21
You might be able to do it with ffmpeg too, like this:
```
ffmpeg -i in.flv -vn -f wav out.wav
```

But, I don't have any flv's so I can't say for sure. But I use that to rip audio from avi files.

---

### Post by FakeOutdoorsman on 2009-03-21
FFmpeg can extract the audio without re-encoding.  This preserves the quality.  First I find out what type of audio is in the file if I don't already know:
```
ffmpeg -i inputfile.flv
```
Along with some other data, it will tell you about the audio:
```
Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 56 kb/s
```
Now I know it is mp3 audio (it usually is mp3 in FLV) I use the following command:
```
ffmpeg -i inputfile.flv -acodec copy output.mp3
```

---

### Post by afeasfaerw23231233 on 2009-07-09
I have 30 .flv files in this folder. How can I extract audio from all files in this folder by ffmpeg using a single command? Also I would like to know how to display the audio information of multiple files by the ffmpeg -i command. Thanks!

---

### Post by unutbu on 2009-07-09
To run "ffmpeg -i" on all the flv files:
```

for j in *.flv; do ffmpeg -i "$j"; done
```

To extract mp3 audio from each flv:
```

for j in *.flv; do ffmpeg -i "$j" -acodec copy "$j".mp3; done; rename 's/flv.mp3$/mp3/' *
```

---

### Post by afeasfaerw23231233 on 2009-07-09
thanks!

---

### Post by ishine on 2009-07-14
It's a good application to extract audio from video files.

---

### Post by llamabr on 2009-09-05
Hmm.  I'm having trouble with my mplayer, then.  I got this vid from youtube, and i can play it in totem, but mplayer complains about unsupported video codec:

```
[flv @ 0x883ec08]Unsupported video codec (7)

```

```
brock@llamakc:~$ file burrito.flv 
burrito.flv: Macromedia Flash Video
brock@llamakc:~$ 

```

What do I do now?  Thanks

---

### Post by ethanay on 2010-02-14
> **FakeOutdoorsman said:**
> FFmpeg can extract the audio without re-encoding.  This preserves the quality.  First I find out what type of audio is in the file if I don't already know:
```
ffmpeg -i inputfile.flv
```
Along with some other data, it will tell you about the audio:
```
Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 56 kb/s
```
Now I know it is mp3 audio (it usually is mp3 in FLV) I use the following command:
```
ffmpeg -i inputfile.flv -acodec copy output.mp3
```

I for the life of me couldn't get a usable audio extraction from a YouTube .flv video containing AAC audio (tried various mplayer/ffmpeg/Avidemux options) without transcoding.  All of them gave me an audio file that would not play.

The above commands worked for me:  :D

```
$ ffmpeg -i 01.flv
Seems stream 0 codec frame rate differs from container frame rate: 49.99 (24997/500) -> 25.00 (25/1)
Input #0, flv, from '01.flv':
  Duration: 00:05:38.36, start: 0.000000, bitrate: 420 kb/s
    Stream #0.0: Video: h264, yuv420p, 480x360 [PAR 1:1 DAR 4:3], 420 kb/s, 25 tbr, 1k tbn, 49.99 tbc
    **Stream #0.1: Audio: aac, 44100 Hz, stereo, s16**
At least one output file must be specified
```

```
$ ffmpeg -i 01.flv -acodec copy 01.aac
```

:popcorn:
THANK YOU!!

PS Here is the source of the original input file:
[http://www.youtube.com/watch?v=31iatVlkAxY](http://www.youtube.com/watch?v=31iatVlkAxY)

---

### Post by runesvend on 2011-04-24
I'd just like to report a solution as well. This will take in a video file, remove the video, and output the audio in an MPEG-4 container:

```
ffmpeg -i inputvideo.mp4 -vn -acodec copy audio.mp4

```

*-vn* removes the video, *-acodec copy* makes it copy the audio instead of re-encoding it.

---

### Post by polardude1983 on 2011-04-24
I always used the program [ClipGrab]("http://www.omgubuntu.co.uk/2010/09/download-youtube-videos-ubuntu-clipgrab/")

---

### Post by darkazurka on 2011-08-01
> **mb_webguy said:**
> {snip}Open VLC and go to Media->Convert/Save.  Open the file you want to strip and click Convert/Save.  At the top, check the File output, and provide a filename and location.  Choose your Encapsulation preference, make sure nothing is selected on the Video tab, check the Audio box on the Audio tab and choose the settings, and click Save.{snip}
In my VLC it is different. (I use version 1.1.9 "The Luggage")

Open VLC (in this case 1.1.9) and click Convert/Save. At the top, click on "Add..." and select your video(example.flv). Click on the button "Convert / Save". Click on "Browse", type a name under "Name:"(example.ogg), select a location to save it to and click on the button "Save". Select a profile that doesn't include any video codec{Audio - Vorbis (OGG)} and click on "Start". The conversion has started and you may notice that your window is now called "Streaming - VLC media player". When the conversion is finished the window will be renamed to "VLC media player".

---

### Post by darkazurka on 2011-08-01
> **polardude1983 said:**
> I always used the program [ClipGrab]("http://www.omgubuntu.co.uk/2010/09/download-youtube-videos-ubuntu-clipgrab/")

I've also just started using it. It is great and specific to the purpose(!) while VLC is a general purpose video related software. I knew VLC was buggy in conversion but I'm glad that they have fixed most conversion bugs by now.

Anyway for this particular purpose of converting a youtube video directly to audio(further improvements could be made so that it converts the video synchronously while it downloads it) ClipGrap is suited for the job!

[http://clipgrab.de/en](http://clipgrab.de/en)

```
sudo add-apt-repository ppa:clipgrab-team/ppa
sudo apt-get update && sudo apt-get install clipgrab
```

The above commands I used to later install this program (GPLv3) that is available from the Applications -> Internet menu.

---

