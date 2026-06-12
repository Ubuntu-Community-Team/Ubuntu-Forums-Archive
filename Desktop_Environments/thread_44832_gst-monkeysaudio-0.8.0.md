---
title: "gst-monkeysaudio-0.8.0"
date: 2005-06-27
forum: Desktop Environments
---

### Post by chungsijay on 2005-06-27
Hello, 
I downloaded gst-monkeysaudio-0.8.0 from here:
[http://gstreamer.freedesktop.org/src/gst-monkeysaudio/](http://gstreamer.freedesktop.org/src/gst-monkeysaudio/)

I compiled amd make to install it
then I try
```
gst-launch-0.8 filesrc location="CDImage.ape" ! monkeysdec ! osssink
```
but failed and eroor messages are here:
> RUNNING pipeline ...
ERROR: from element /pipeline0/monkeysdec0: Internal GStreamer error: pad problem.  File a bug.
Additional debug info:
gstpad.c(2563): gst_pad_set_explicit_caps: /pipeline0/monkeysdec0:
failed to negotiate (try_set_caps with "audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)16, depth=(int)16, rate=(int)24, channels=(int)0" returned REFUSED)

does someone use gst-monkeysaudio-0.8.0 and have the same problem?
and How to solve it?  
Any advice will be appreciated.

---

