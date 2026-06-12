---
title: "mplayer/ mencoder record and play webcam and audio"
date: 2009-03-29
forum: General Help
---

### Post by rfrayer on 2009-03-29
ok I was wondering if someone could pelase help me with somthing

Ive gotten mencoder to be able to rip a video using my usb webcam/mic by logitech and the qaulity is awsome.

what id like to do is have mplayer pop up at the same time playing/monitoring the stream as it records.. heres the code imj using for mencoder 

```

mencoder tv:// -tv driver=v4l:width=320:height=240:device=/dev/video1:forceaudio:adevice=/dev/dsp2 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o webcam.avi

```

---

### Post by andrew.46 on 2009-03-29
Hi rfayer,

> **rfrayer said:**
> Ive gotten mencoder to be able to rip a video using my usb webcam/mic by logitech and the qaulity is awsome.

what id like to do is have mplayer pop up at the same time playing/monitoring the stream as it records.. heres the code imj using for mencoder 
```

mencoder tv:// -tv driver=v4l:width=320:height=240:device=/dev/video1:forceaudio:adevice=/dev/dsp2 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o webcam.avi

```


I have not tested this fully but I believe the following is one way that might be worth a look at:

```

mencoder tv:// \
   -tv driver=v4l:width=320:height=240:device=/dev/video1:forceaudio:adevice=/dev/dsp2 \
   -ovc lavc \
   -oac mp3lame -lameopts cbr:br=64:mode=3 \
   -o >(tee webcam.avi | mplayer -)

```

My apologies for not testing this one properly, I do not have device to capture from really, crossing my fingers that it works for you :-). BTW have you thought of adding a few -lavcopts to your output video?

Andrew

---

### Post by josvanr on 2011-01-17
mencoder tv:// -tv driver=v4l2:width=320:height=240:device=/dev/video1:forceaudio:adevice=/dev/dsp1:brightness=90:volume=35000 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o > mplayer -


tryin this for starters, but no, the mplayer window doesnt 
pop up. In terminal I see:

1 duplicate frame(s)!

4 duplicate frame(s)!

3 duplicate frame(s)!

3 duplicate frame(s)!

2 duplicate frame(s)!


etc




josvanr

---

### Post by josvanr on 2011-01-17
argh.. spent another day on this. but it still seems to 
be simply impossible to view and record from webcam
at the same time,well using mplayer&mencoder anyway
 (tried using mkfifo stream.yuv and
pipe-ing but... nop)

josvanr

---

### Post by dfoxpro on 2011-11-05
Im worked o it (tv input) last week and i wrote this script:

mencoder \
-tv driver=v4l2:device=/dev/video0:input=0:normid=0:alsa:adevice=hw.2:amode=1:audiorate=32000:immediatemode=0:width=496:height=371:chanlist=us-cable  \
-ovc lavc -lavcopts vcodec=mpeg4:vhq:vbitrate=600 \
-oac mp3lame -lameopts cbr:br=64 \
tv:// \
-o $PATH1/${TODAY}_${NOW}_CH.mp4 &
sleep 1
mplayer $PATH1/${TODAY}_${NOW}_CH.mp4 -vo xv
killall mencoder



to view all i do see and comment:
[http://trucos-ubuntu.blogspot.com/](http://trucos-ubuntu.blogspot.com/)
[http://dl.dropbox.com/u/7360282/ubuntucosas/rec.sh](http://dl.dropbox.com/u/7360282/ubuntucosas/rec.sh) (i blind this script to a remote key)

---

### Post by josvanr on 2012-01-08
hello

thnx for your reply (I realize it has been some time)

but I don't understand: your script seems to record one second of 
webcam to a file and then play that with mplayer..? Whatis 
it supposed to do?


josvanr


> **dfoxpro said:**
> Im worked o it (tv input) last week and i wrote this script:

mencoder \
-tv driver=v4l2:device=/dev/video0:input=0:normid=0:alsa:adevice=hw.2:amode=1:audiorate=32000:immediatemode=0:width=496:height=371:chanlist=us-cable  \
-ovc lavc -lavcopts vcodec=mpeg4:vhq:vbitrate=600 \
-oac mp3lame -lameopts cbr:br=64 \
tv:// \
-o $PATH1/${TODAY}_${NOW}_CH.mp4 &
sleep 1
mplayer $PATH1/${TODAY}_${NOW}_CH.mp4 -vo xv
killall mencoder



to view all i do see and comment:
[http://trucos-ubuntu.blogspot.com/](http://trucos-ubuntu.blogspot.com/)
[http://dl.dropbox.com/u/7360282/ubuntucosas/rec.sh](http://dl.dropbox.com/u/7360282/ubuntucosas/rec.sh) (i blind this script to a remote key)

---

