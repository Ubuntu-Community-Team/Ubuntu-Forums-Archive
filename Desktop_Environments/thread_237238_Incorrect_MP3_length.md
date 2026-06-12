---
title: "Incorrect MP3 length"
date: 2006-08-15
forum: Desktop Environments
---

### Post by pertti on 2006-08-15
Hi, I've been reencoding my CD collection with Sound Juicer, and now I just found out that the length of many of the songs aren't right. On Rhythmbox some song show as if they were over 10 minutes. If I open one of those songs with Totem I can see that 10-something length for a second in the status bar, but then it changes to the right length.

I tried running checkmp3 with some of this files, and it reports the correct length, so I'm a bit puzzled:

```
Possible ID3v2 frame found, skipping

FILE_NAME           01-Debaser.mp3
GOOD_FRAMES         6631
BAD_FRAMES          0
LAST_BYTE_CHECKED   4243185
VBR_HIGH            320
VBR_LOW             32
VBR_AVERAGE         196
SONG_LENGTH         02:53.21
```

By the way, this is the GStreamer profile which I used to encode those CDs:

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=standard ! id3v2mux
```

Is there any way to correct the song length of these MP3 files? I guess that this is due to some tag info being wrong, but I can't edit the song length with EasyMP3 (which also shows the incorrect length).

Thanks in advance!

---

### Post by reacocard on 2006-08-15
try this pipeline:
```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=4 vbr-quality=2 bitrate=160 ! xingmux ! id3v2mux
```
it's the one i use. there's a lot of stuff in there, but the important part for you is "xingmux", which writes tags that are more compatible with recent players.

(Just in case you're wondering, my pipeline also enables vbr and increases the bitrate to 160kbps)

---

### Post by pertti on 2006-08-16
Thanks for the pipeline, but it produces the same result: incorrect song length :(. I also noticed that gtkpod gets the length right. Quite odd...

On a side note, both id3v2mux and xingmux write tags that can be read with Totem or Rhythmbox (both GStreamer 0.10), but not with EasyTag or AudioTagTool, which I use to complete some information about the songs. A bit annoying as well.

Maybe these problems are related. I mean, maybe from the GStreamer pipeline to the music player someone is not getting/setting the tags right. Just a thought.

---

### Post by pertti on 2006-08-24
Sorry to *bump* this.

After transfering some of these songs to my iPod Nano (using gtkpod), even though the songs show the correct length, if I do any fast forward/backward it doesn't land at the specified time, but rather before that point. However, the song ends when it reaches the specified length, event though it's still playing halfway through.

For example, some song lasts 4:00. If when at 2:00 I forward to 3:00, the song really jumps to, say, 1:30, but the interface shows 3:00. One minute later the interface reaches 4:00 and the song stops, but it really was at 2:30 when it stopped. (Sorry if it's a bit confusing :) )

This is quite annoying, and I have found this MP3 length problem with the few GStreamer pipes I've tried.

Any idea? Blame GStreamer or SoundJuicer? Gtkpod or iPod? Vim or emacs? ;)

Thanks in advance

---

### Post by padre999 on 2006-09-01
Same problem here :( 

Somehow the mp3s are incorrectly tagged with a bitrate of 32 kbps (some 128 kbs) which is obviously not the case. At least thats what amarok and other players show in the files properties. They sound much better than 32 kbps and the file size is much bigger.

I use the same pipe as pertti: 
```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=standard ! id3v2mux
```
Any ideas?

---

### Post by pertti on 2006-09-01
I thought I was the only one who has this problem. Sorry to hear from you ;). OK, some updated info on the problem.

I tried [the MP3 CBR pipeline on the Ubuntu Wiki]("https://help.ubuntu.com/community/CDRipping#head-f109ee313aa77bf2997e6499584438e9f7691d58") and everything went well, but the VBR pipeline on that same page doesn't work as well (it also uses --preset standard, but with a different argument).

Then I tried using lame from the command line to encode a .wav file ripped using Grip. I ended up with a .mp3 larger than the one I got from  SoundJuicer (6.0 MB vs. 6.4 MB), but the file has the correct length. The command I used was:

```
lame --preset standard the_clock.wav The\ Clock.mp3
```

Also an update with the iPod thing. I just have to pause the song to make the song position go crazy. Quite annoying :(.

So:

[LIST]
[*]lame from command line + VBR = good
[*]lame in a Gstreamer pipeline + CBR = good
[*]lame in a GStreamer pipeline + VBR = bad
[/LIST]

Is it then a bug in GStreamer?

---

### Post by eindgebruiker on 2006-09-16
I encountered the same problem. If I add "xingmux", as described above, I get the following results:

- the bitrate is shown correctly in Nautilus, Totem and Rhythmbox
- the length is shown correctly in Rhythmbox
- the length is wrong in Totem and Nautilus

checkmp3 test.mp3:

```
Possible ID3v2 frame found, skipping

An expected frame was not found. Expected it at offset 0x7f5 (BYTE 2037), now at offset 0x997 (BYTE 2455).
FILE_NAME           test.mp3
GOOD_FRAMES         10279
BAD_FRAMES          1
LAST_BYTE_CHECKED   5385098
VBR_HIGH            256
VBR_LOW             32
VBR_AVERAGE         160
SONG_LENGTH         04:28.53
```

---

### Post by eindgebruiker on 2006-09-16
Bug report:

[https://launchpad.net/distros/ubuntu/+source/gst-plugins-ugly0.10/+bug/35112](https://launchpad.net/distros/ubuntu/+source/gst-plugins-ugly0.10/+bug/35112)

---

### Post by klato on 2006-12-26
Looks like this is still a bug...I've been trying to get correct VBR track length using the gstreamer pipeline all day and I can't figure it out...I might just take my CDs to work tomorrow and rip em all using iTunes! :(

---

### Post by o_fortuna on 2007-01-18
Oh good, I'm not the only one having this problem.

It doesn't make sense. I tried the xigmux thingy, but now Rhythmbox gives me a MIME error and Totem changes the song length constantly (due to the changing bitrate, I guess).

BUT!!!!

The bug is marked as fixed. :(

Any help for a poor helpless soul forced to use the lesser quality of the iTunes mp3 encoder?

---

### Post by minivitale on 2008-05-23
Somebody reported that rhythmbox was working properly while totem would not find the proper length. I am having just the opposite problem: totem has no trouble seeing that an mp3 is about 30 minutes long, while rhythmbox calls it 17!

As far as fixing it i have no idea, i just figured i would add my data to this list.

---

