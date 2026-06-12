---
title: "amarok problem"
date: 2006-04-28
forum: Desktop Environments
---

### Post by brucech85 on 2006-04-28
When i try running amarok, which i have been doing for the past few months with no prolems , it loads then crashes and i get this error message;

amaroK has crashed! We're terribly sorry about this :(

But, all is not lost! You could potentially help us fix the crash. amaroK has attached a backtrace that describes the crash, so just click send, or if you have time, write a brief description of how the crash happened first.

Many thanks.

Engine:     gst-engine
Build date: Oct  4 2005
CC version: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
KDElibs:    3.4.2
TagLib:     1.3.1
NDEBUG:     true

i think it may be due to having installed more than one g-streamer...

any ideas on how to solve this problem ?

---

### Post by kaptainlange on 2006-04-28
I couldn't tell you why it is crashing, however I have had problems with the gstreamer engine in amarok in the past.  If you're interested in simply getting amarok to work, you could try install the xine engine which is what I currently use.

```
sudo apt-get install amarok-xine
```

Then under amarok's preferences, change the engine to xine from gstreamer.

---

