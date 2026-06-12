---
title: "Dell XPS 1530 webcam problem"
date: 2008-06-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rosarioarun on 2008-06-20
I googled and also searched the ubuntu forum i couldnt find a solution to recover my problem

I want to use my webcam
I tried the package webcam the output when i tried is

  root@ros-lap:/home/rosarioarun# webcam
  reading config file: /root/.webcamrc
  video4linux webcam v1.5 - (c) 1998-2002 Gerd Knorr 
    grabber config:
  size 320x240 [16 bit YUV 4:2:2 (packed, YUYV)]
  input (null), norm (null), jpeg quality 75
  rotate=0, top=0, left=0, bottom=240, right=320
   ioctl: VIDIOC_DQBUF(index=0;type=VIDEO_CAPTURE;bytesused=0;flags=0x0     [];field=ANY;;timecode.type=0;timecode.flags=0;timecode.frames=0;timecode.seconds=0;timecode.minutes=0;timecode.hours=0;timecode.userbits="";sequence=0;memory=unknown): Invalid argument
capturing image failed




i then tried the command
     mplayer tv:// -tv driver=v4l2:width=640:height=480:device=/dev/video0 -fps 30

Error is like: v4l2: ioctl dequeue buffer failed: Invalid argument, idx = 0

both went invain. Got those commands from net. Help me out how to use my web cam. my lsmod output is below.

---

### Post by falcon61102 on 2008-07-07
Don't know if you were able to find a solution to this yet, but I know some others with an XPS had issues with there webcam and installing Cheese took care of it for whatever reason.  I don't know if mine worked before installing Cheese as I installed it right after a fresh install but it works now, might be worth a try for you.

---

### Post by Henery on 2009-08-01
Yes this worked for me anyway just installed cheese and my cam works on a xps 1530!
Thank you for the tip this is a great forum!

---

