---
title: "gstreamer pipelines"
date: 2006-10-03
forum: Desktop Environments
---

### Post by markcarey on 2006-10-03
Hi,

I am trying to convert mpeg2 captures from a Hauppage WinTV PVR150 under ubuntu dapper into an mpeg1 stream using gstreamer.

I will eventually edit the stream to remove unwanted segments. I have been unable to find a package for on ubuntu which allows direct editing of mpeg2 streams.

I am attempting to use gstreamer for the conversion with the fluendo mpeg codec.  Trying to get the video only working for now, with the attached ... and getting the following error.

careys@jersey:/video$ gst-launch-0.10 filesrc location=20061002-2130-2-greys.mpg ! flupsdemux ! mpeg/video,mpegversion=1 ! filesink location=out1.mpeg
Setting pipeline to PAUSED ...
Pipeline is PREROLLING ...

(gst-launch-0.10:15653): GStreamer-CRITICAL **:
Trying to dispose element capsfilter1, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.


(gst-launch-0.10:15653): GStreamer-CRITICAL **:
Trying to dispose element capsfilter2, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.

Any thoughts/suggestions?

Thanks ......

Mark Carey

---

