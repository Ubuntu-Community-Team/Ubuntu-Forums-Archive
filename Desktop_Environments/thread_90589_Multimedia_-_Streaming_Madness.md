---
title: "Multimedia - Streaming Madness"
date: 2005-11-15
forum: Desktop Environments
---

### Post by Ingla on 2005-11-15
Hello.

I'm a newbie, running Ubuntu 5.10.

I've had a lot of trouble getting streaming to work.

Sometimes something works directly on Firefox...usually not.

I have the following programs installed:

[COLOR="Blue"]gmplayer
gxine
mplayer
Totem
VLC
xine
XMMS[/COLOR]

[COLOR="Red"]QUESTION 1.[/COLOR]
For a while, VLC could play most any radio stream. It seems to have gone nuts. Now, whatever I ask it to play, it just keeps running up and down the playlist and is unable to do anything. OR, if asked to play a specific stream, it looks for a few seconds like it's trying and then goes blank...and occasionally hangs.

I discovered that XMMS could play all of the streams. I was listening to one, when I tried to save a playlist. From that moment on, it hasn't been able to play anything. If I try to open a stream, it might momentarily show the address it's trying to get (without playing anything), but, more often, it just sits there looking at me. System Monitor says it's sleeping!

Mplayer and xine usually say they can't find a plugin, although I think I've installed every one known to man.

What on earth is the matter with these Linux programs? One minute, everything's fine...and the next, Goodbye!

[COLOR="Red"]QUESTION 2.[/COLOR]

Right now, I can't play anything unless Firefox feels up to it.

If it's any help, the plugins Firefox says it has are:

---------------------------------------------------------------------------------------------------------------


[COLOR="Blue"]gxine starter plugin

File name: gxineplugin.so
will start external gxine media player for embedded media streams
------------------------------------------
Shockwave Flash

File name: libflashplayer.so
Shockwave Flash 7.0 r25
------------------------------------------
VLC multimedia plugin

File name: libvlcplugin.so
VLC multimedia plugin
------------------------------------------
OpenOffice.org Plug-in

File name: libnpsoplugin.so
------------------------------------------
Totem Mozilla Plugin

File name: libtotem_mozilla.so
------------------------------------------
Google VLC multimedia plugin 1.0

File name: mplayerplug-in-gmp.so
mplayerplug-in 3.05
-------------------------------------------
QuickTime Plug-in 6.0

File name: mplayerplug-in-qt.so
mplayerplug-in 3.05
-------------------------------------------
RealPlayer 9

File name: mplayerplug-in-rm.so
mplayerplug-in 3.05
-------------------------------------------
Windows Media Player Plugin

File name: mplayerplug-in-wmp.so
mplayerplug-in 3.05
-------------------------------------------
mplayerplug-in 3.05

File name: mplayerplug-in.so
mplayerplug-in 3.05
-------------------------------------------
Java(TM) Plug-in 1.5.0_05-b05

File name: libjavaplugin_oji.so
Java(TM) Plug-in 1.5.0_05[/COLOR]
-------------------------------------------------------------------------------------------------------------
I have to boot to Windows to hear anything.

Anyone have any ideas on any of this?

Thanks.

---

### Post by Dr. Nick on 2005-11-15
you having trouble with video aswell or just audio? If video is messed up and trying to open in totem then  look up automtix [here]("http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix") or jsut manually move the totem plugin out of firefox.

The mplayer may handle audio aswell, not sure

---

### Post by Ingla on 2005-11-15
Hi.

Video was working in gzine for streaming TV. Now it can't play it.

Also, as mentioned, none of the programs is working on the system...not counting Firefox problems. I go out of Firefox and open one of the media programs and it won't play anything.

As far as I know, this happened spotaneously. I didn't install any plugins, programs, codecs, etc. UNLESS some install which had nothing to do with multimedia creamed some dependencies or something.

I don't know where to begin to sort this out.

Anybody?

---

### Post by bronwe on 2005-11-17
Hey All,

I newly installed Breezy, and want streaming audio using Firefox and Totem, because I want to listen to Amazon's audio samples before I buy CDs.

Is there a plugin?  Do I need w32codecs?  

What is the easiest way to use Totem to do this.

-Bronwe

---

### Post by raven on 2005-11-20
unfortunatley I have a problem with streaming too
I can play OTHER streaming (mms) audio but not this one
this is the main site [http://www.batanga.com](http://www.batanga.com), the stations are on the left, on the bottom left it have instruction on how to play it in linux, basically they gives you the direct link to the stream which is this one,
mms://wm.batanga.com/BATANGA_Brazilian_126
explanation are in spanish

can any body check if he/she can play it on breezy
winxp plays no problem while at the same time breezy cannot
used mplyer terminal, vlc terminal, totem xine,
kaffeine, all cannot play it

message in terminal for mplayer

```
playing mms://wm.batanga.com/BATANGA_Brazilian_126.
STREAM_ASF, URL: mms://wm.batanga.com/BATANGA_Brazilian_126
Resolving wm.batanga.com for AF_INET6...
Couldn't resolve name for AF_INET6: wm.batanga.com
Resolving wm.batanga.com for AF_INET...
Connecting to server wm.batanga.com[38.116.36.26]:1755 ...
connected
unknown object
unknown object
unknown object
unknown object
file object, packet length = 1053 (1053)
unknown object
stream object, stream id: 1
stream object, stream id: 2
data object
mmst packet_length = 1053
Cache size set to 1024 KBytes
Cache fill: 19.53% (204800 bytes)    ASF file format detected.
Clip info:
 name: Radio Brasil
 author: Batanga
 copyright: (c) 2005 Batanga
 comments: Radio Brasil 22kbps
==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22050 Hz, 2 ch, s16le, 22.0 kbit/3.12% (ratio: 2751->88200)
Selected audio codec: [ffwmav2] afm:ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
Building audio filter chain for 22050Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 22050 Hz/2 channels/4 bpf/30104 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 22050Hz 2ch s16le (2 bps)
Building audio filter chain for 22050Hz/2ch/s16le -> 22050Hz/2ch/s16le...
Video: no video
Starting playback...
A:  -0.0 (00.0) ??,?% 0%
```

than it hangs

error messages from the messages box of vlc
attached as a file from "messages"


any help ?

---

### Post by Caro_CR on 2007-11-04
[http://radio.batanga.com/sp/linuxusers.asp](http://radio.batanga.com/sp/linuxusers.asp)

There you can open the windows streaming and firefox opens it. 

I tried with totem but it did not work.

---

