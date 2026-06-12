---
title: "Is .ram to .mp3 possible?"
date: 2006-06-24
forum: Desktop Environments
---

### Post by Kouya on 2006-06-24
I was wondering... using mplayer I've dl streamed media to my hardrive but I wan to put them in my mp3 player. Is there anyway to convert the .ram files to .mp3?

---

### Post by firebadger on 2006-06-24
Hi, 

.ram files are playlist files, they just contain a url to the actual stream.  You can use a command like this to download the stream and store as a wav (assumes the playlist file is called playlist.ram).

[FONT="Courier New"]mplayer -playlist playlist.ram -ao pcm -ao pcm:file=tmp.wav -vc dummy -vo null[/FONT] 

Once you have a wav file, it's easy to convert to the compressed format of your choice using lame (for mp3s) or oggenc (for ogg).  You could also use a tagging program to tag them appropriately.  Writing a script to do all that automatically would be quite handy.

---

### Post by Kouya on 2006-06-24
many thanks!! ... I'll go give it a shot! :D

---

### Post by Kimm on 2006-06-24
You can also use:

mplayer -dumpstream <stream>

to record streaming audio (and video?). The song will then be inside "stream.dump" (same format as the stream)

then use:
mplayer stream.dump -ao pcm:file=ripped_audio.wav

to convert to wav.

Then you can use Audacity (or similar) to convert to mp3 (/ogg).

Note:
you may loose sound quality when converting from one "lossy" format (like mp3, ogg, or Real Audio) to another. Converting to/from wav and Flac is "safe" though.

---

