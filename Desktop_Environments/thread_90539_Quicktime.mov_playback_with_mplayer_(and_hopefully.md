---
title: "Quicktime/.mov playback with mplayer (and hopefully Kaffeine)"
date: 2005-11-15
forum: Desktop Environments
---

### Post by authortitle on 2005-11-15
Hey,

I'm trying to get Windows video formats to play back (mainly DivX, WMV and Quicktime). I've installed the w32-codecs package, and DivX, XVid and WMV play fine with mplayer. However, when I play a .mov (QuickTime) file, no matter the resolution of it, it plays back too slowly, the sound plays in small "chunks", and many messages like alsa-space: xrun of at least 0.092 msecs. resetting stream?,?% 0 0 91% appear - I presume this is a sound related error?

Some more sound details -

AUDIO: 22050 Hz, 1 ch, s16le, 23.9 kbit/6.79% (ratio: 2993->44100)
Selected audio codec: [qdmc] afm:qtaudio (QuickTime QDMC/QDM2 audio decoders)
...
alsa: 22050 Hz/1 channels/2 bpf/15052 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 22050Hz 1ch s16le (2 bps)

Anyone clever enough to figure this out? Smiley Or at least, anyone got QT playback working fine?

And also (this may be easier to sort out) how can I get these codecs to be recognised in Kaffeine (so I suppose, how can I get gstreamer to recognise them)? The sound plays but the video doesn't, for formats that do work with mplayer.

Any help appreciated,

Cheers,
Tom

---

### Post by Pablo_Escobar on 2005-11-15
My quicktime files play great (gotta love them trailers) :)

About Your problem, I don't if this thing will help You out, but maybe You're missing tha package called 
> libquicktime1
It's in Ubuntu repos.

Hope maybe this will help.

---

### Post by authortitle on 2005-11-15
I was missing that package, just installed it but it makes no difference.

I take it you are using w32codecs to get QuickTime to playback? Which version of w32codecs do you have? Mine is 1:20050412-0.0... maybe this is where the problem lies. No other format seems to have any issues.

Hope I get this sorted, don't want to have to boot back in to Windows :)

Cheers,
Tom

---

### Post by Pablo_Escobar on 2005-11-15
Heck, missed shot :(
I'm not on my Ubuntu box right now, but my version is taken from PLF repos. Later on I can paste my version.
About Your problem, if other formats play well, then it can be quicktime-sound configuration problem.
I'll try to fiddle something at home, and report back if someone doesn't solve Your problem till then.
Don't even think about getting back at dreaded M$ :D

---

### Post by Pablo_Escobar on 2005-11-15
Heh, my w32codecs is the same as Yours.
That leaves the quicktime sound configuration problem. I don't know what can be the cause of this problem :(

---

### Post by authortitle on 2005-11-16
Thanks for checking that.

I read around the net a bit more, a few other people had the problem and didn't seem to have found a "proper" solution, but one of two things will do it: either use ESD instead of ALSA (add -o esd to the mplayer command line) or use srate=48000 (it defaults to 44100) - I just added srate=48000 to my ~/.mplayer/config and it all seems fine :)

Thanks!
Tom

---

