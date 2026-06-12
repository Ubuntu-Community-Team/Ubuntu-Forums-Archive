---
title: "Audio levels in DVD ripping"
date: 2006-04-18
forum: Desktop Environments
---

### Post by deadgoon on 2006-04-18
SOLVED - see post #2 below!

I just ripped an audio track from one of my concert DVDs according to the instructions in the post I have quoted below.  However, the audio levels are extremely low.  What I mean is that I have to turn the volume WAY up in comparison to my other music.  Is there a way to increase the audio levels when I rip the audio from my DVD?


[QUOTE=flaming_monkey]Good old mplayer to the rescue.

Ensuring you have libdvd and mplayer installed, find the chapter you want to rip.
```

$ mplayer dvd://1
$ mplayer dvd://2
$ mplayer dvd://3 ... etc.

```

Once you've found the chapter you want to rip use the following options:

```

$ mplayer dvd://1 -vc dummy -vo null -af resample=44100 -ao pcm:file=ripped-audio.wav

```

The output .wav file can then be compressed with lame or oggenc

```

$ oggenc -q4 ripped-audio.wav -o ripped-audio.ogg

```[/QUOTE]

---

### Post by deadgoon on 2006-04-18
After some research I discovered the solution to my own problem.

I used a combination of acidrip, ffmpeg, and oggenc to do the ripping.  All are available through apt.

First I extracted each chapter to an avi file using Acidrip.  On the Video tab I set the Codec to "copy".  On the General tab I set the audio codec to "pcm" and the gain to 18 (this can be any number, experiment to see what works for you).  Then I used the preview tab to check the audio levels.  Then I queued up all the chapters and started ripping.

Once the avi files were made I used the following ffmpeg command to extract the audio to a wav file.

```
ffmpeg -i filename.avi filename.wav
```

Once I had done this, I used oggenc to make ogg files.

```
oggenc -q6 filename.wav -o filename.ogg
```

Here's the bash script for that last step and it can also be used for the ffmpeg step as well.

```

#!/bin/sh
for i in *.wav
do
  oggenc -q6 $i -o `basename $i .wav`.ogg
done

```

Now I just need to learn to use Audacity to strip out the talking on the tracks!

---

