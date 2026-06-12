---
title: "MythTV, ATI, Xine, TVout"
date: 2006-01-24
forum: Desktop Environments
---

### Post by xinman on 2006-01-24
I believe my problem is with Xine.  But I'm not possitive.  I have MythTV working great, I have the ATI 9800 Pro card and the fglrx drivers are installed and working nicely.  Xine is installed, with DVD Support and LIRC support.  TV-OUT is working pretty well, need to tweek the resolutions a little.  The problem is when I try to watch TV, or VCD, or anything that uses Xine, the screen on the TV goes black, and the monitor still has video.  Mplayer plays to the TV, but Xine doesn't.  I want Xine support for DVD Menus mostly.  Anyone know how to remedy this situation?

All help is highly appreciated!
Thanks,
Dan

---

### Post by xinman on 2006-01-24
Ok, I've got everything working in Mythtv including TV out for DVD and Videos, except for TV...  Really weird but dvd's play to my tv, divx videos play to my tv, but tv only goes to my monitor, sound goes out to the tv, but no video.
Here is the verbose log of mythtv
```
2006-01-24 22:00:32.567 New DB connection, total: 1
Total desktop width=800, height=600, numscreens=1
2006-01-24 22:00:32.572 Using screen 0, 800x600 at 0,0
2006-01-24 22:00:32.575 mythfrontend version: 0.18.1.20050510-1 www.mythtv.org
2006-01-24 22:00:32.576 Enabled verbose msgs : important general playback
2006-01-24 22:00:32.738 Switching to square mode (blue)
2006-01-24 22:00:33.011 New DB connection, total: 2
2006-01-24 22:00:33.013 Joystick disabled.
2006-01-24 22:00:33.050 Registering Internal as a media playback plugin.
2006-01-24 22:00:33.068 Registering MythDVD DVD Media Handler as a media handler
2006-01-24 22:00:33.201 Registering MythMusic Media Handler as a media handler
2006-01-24 22:00:34.641 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2006-01-24 22:00:34.649 Using protocol version 15
2006-01-24 22:00:37.423 Using protocol version 15
2006-01-24 22:00:39.451 AVFD
2006-01-24 22:00:39.451 AVFD: Opening Stream #0: codec id 2
2006-01-24 22:00:39.453 detectInterlace(Detect Scan, Detect Scan, 29.97, 480) ->Interlaced Scan
2006-01-24 22:00:39.453 Interlaced: Interlaced Scan  video_height: 480  fps: 29.97
2006-01-24 22:00:39.453 AVFD: Looking for decoder for 2
2006-01-24 22:00:39.453 AVFD
2006-01-24 22:00:39.453 AVFD: Opening Stream #1: codec id 86016
2006-01-24 22:00:39.454 AVFD: Looking for decoder for 86016
2006-01-24 22:00:39.661 Estimated bitrate = 6384
2006-01-24 22:00:39.668 Filling position map from 0 to 38
2006-01-24 22:00:39.676 Position map filled from Encoder to: 2
2006-01-24 22:00:39.676 SyncPositionMap liveTV, from Encoder: 3 entries
2006-01-24 22:00:39.677 SyncPositionMap, new totframes: 30, new length: 1, posMap size: 3
2006-01-24 22:00:39.677 Partial position map found
2006-01-24 22:00:39.680 Opening audio device '/dev/dsp'.
2006-01-24 22:00:39.681 Opening OSS audio device '/dev/dsp'.
2006-01-24 22:00:39.690 Over/underscan. V: 0, H: 0, XOff: 0, YOff: 0
2006-01-24 22:00:39.697 Using XV port 115
2006-01-24 22:00:39.702 Image size. dispxoff 0, dispyoff: 0, dispwoff: 800, disphoff: 600
2006-01-24 22:00:39.702 Image size. imgx 0, imgy: 0, imgw: 480, imgh: 480
2006-01-24 22:00:39.982 Realtime priority would require SUID as root.
2006-01-24 22:00:40.002 Changing from None to WatchingLiveTV
2006-01-24 22:00:40.012 nVidiaVideoSync: Could not open device /dev/nvidia0, No such file or directory
2006-01-24 22:00:40.012 DRMVideoSync: VBlank ioctl did not work, unimplemented in this driver?
2006-01-24 22:00:40.012 RTCVideoSync: Could not set RTC frequency, Permission denied.
2006-01-24 22:00:40.013 Using audio as timebase
2006-01-24 22:00:40.013 Video timing method: USleep with busy wait
2006-01-24 22:00:40.014 Refresh rate: 16579, frame interval: 33366
2006-01-24 22:00:40.014 waiting for prebuffer...
2006-01-24 22:00:40.163 A/V diverged by -3.01247 frames, dropping frame to keep audio in sync
2006-01-24 22:00:40.176 HandleGopStart: gopset not set, syncing positionMap
2006-01-24 22:00:40.181 Filling position map from 3 to 3
2006-01-24 22:00:40.192 Position map filled from Encoder to: 3
2006-01-24 22:00:40.192 SyncPositionMap liveTV, from Encoder: 4 entries
2006-01-24 22:00:40.192 SyncPositionMap, new totframes: 45, new length: 1, posMap size: 4
2006-01-24 22:00:40.193 Stream initial keyframedist: 15.
2006-01-24 22:00:40.231 A/V diverged by -3.03755 frames, dropping frame to keep audio in sync
2006-01-24 22:00:40.296 A/V diverged by -3.04978 frames, dropping frame to keep audio in sync
2006-01-24 22:00:40.363 A/V diverged by -3.05104 frames, dropping frame to keep audio in sync
2006-01-24 22:00:40.446 A/V diverged by -3.17913 frames, dropping frame to keep audio in sync
2006-01-24 22:00:40.446 A/V diverged by -3.12612 frames, dropping frame to keep audio in sync
2006-01-24 22:00:40.446 A/V diverged by -3.17913 frames, dropping frame to keep audio in sync
2006-01-24 22:00:40.446 A/V diverged by -3.12612 frames, dropping frame to keep audio in sync
2006-01-24 22:00:40.447 positionMap[ 3 ] == 960550.
2006-01-24 22:00:40.957 positionMap[ 4 ] == 1298470.
2006-01-24 22:00:41.355 positionMap[ 5 ] == 1640486.
2006-01-24 22:00:41.893 positionMap[ 6 ] == 2009126.
2006-01-24 22:00:42.468 positionMap[ 7 ] == 2344998.
2006-01-24 22:00:43.038 positionMap[ 8 ] == 2672678.
2006-01-24 22:00:43.451 Changing from WatchingLiveTV to None
2006-01-24 22:00:43.463 Changing from None to None

```

Any thoughts, please!!!

---

### Post by xinman on 2006-01-25
Okay well since no one else answered I will post the fix.

Unplug the monitor from the video card, seems crazy that all the other video sources would play, not the tv, but if I unplug the monitor before boot up it works and it works great.

---

