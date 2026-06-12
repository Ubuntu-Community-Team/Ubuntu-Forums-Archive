---
title: "no webcam 8.10 amd64"
date: 2009-03-05
forum: General Help
---

### Post by a_toff on 2009-03-05
Hi, I'm running 64-bit 8.10 on a HP Pavillion tx2500 (tx2617ca), and I can't get the internal webcam working.

Here's the error message from the "Multimedia Systems Selector": 

```
Video for Linux 2 (v4l2): Cannot identify device '/dev/video0'.
```

Here is my output from the video test function under "Multimedia Systems Selector":

```
$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /GstPipeline:pipeline0/GstV4lSrc:v4lsrc2]
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannotidentify device '/dev/video0'. [v4l2_calls.c(463): gst_v4l2_open (): /GstPipeline:pipeline2/GstV4l2Src:v4l2src4:
system error: No such file or directory]

```

When I run Camorama, the error message is as follows:

```
Could not connect to video device (/dev/video0). Please check connection.
```

---

