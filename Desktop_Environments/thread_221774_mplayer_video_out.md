---
title: "mplayer video out"
date: 2006-07-24
forum: Desktop Environments
---

### Post by evaristegalois on 2006-07-24
I installed mplayer. It works fine with audio files but refuses to do video. The error message is 

The selected video_out device is incompatible with this codec

no matter whether I want it to play a DVD or a video file.

If I type 
mplayer -vo help

it gives me the following options for video_out devices:

MPlayer 1.0pre8-4.0.3 (C) 2000-2006 MPlayer Team
CPU:         Intel(R) Pentium(R) M processor 1500MHz (Family: 6, Model: 9, Stepping: 5)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Available video output drivers:
	fbdev	Framebuffer Device
	fbdev2	Framebuffer Device
	cvidix	console VIDIX
	null	Null video output
	mpegpes	Mpeg-PES to DVB card
	yuv4mpeg	yuv4mpeg output for mjpegtools
	tga	Targa output
	pnm	PPM/PGM/PGMYUV file
	md5sum	md5sum of each frame

I can try them by typing, for example,

mplayer filename.MOV -vo null

which works fine because null means no video output at all. All I hear is the sound.

My question is: how can I install another video_out device that will work? Or do I need to tweak the ones that I have?

I just upgraded to dapper, and this thing worked really well on breezy:( 

--evaristegalois

---

### Post by evaristegalois on 2006-07-24
it seems that x11 (which is part of dapper) is a possible video out. But how do I tell mplayer that it's there? Even installing mplayer with 
./configure --enable-x11 
didn't do the trick. still, i can only see the above listed video outputs and none of them work.

--evaristegalois

---

### Post by Tsukasa on 2006-07-24
If you compile Mplayer yourself be sure to have the necessary dependencies (dev-files!) installed so you can enable the options.

I'd recommend to enable universe and multiverse repository and get all the necessary dependencies automatically: 
apt-get build-dep mplayer

After that run configure again, you should notice that the standard outputs like xv, x11 or gl should be enabled by default now.

---

### Post by evaristegalois on 2006-07-24
Thank you, Tsukasa. That's what I did, and it's working!

--evaristegalois

---

