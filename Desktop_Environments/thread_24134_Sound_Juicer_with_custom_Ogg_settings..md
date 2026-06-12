---
title: "Sound Juicer with custom Ogg settings."
date: 2005-04-05
forum: Desktop Environments
---

### Post by lewiz on 2005-04-05
I've got a little iRiver iFP899 that supports Ogg playback, which is great.  Problem is the CPU can't handle Oggs with bitrates >250Kbit, which Sound Juicer seems to generate with the default options.  I could drop the quality lower, but I don't really want to do that -- it is very rare that the player can't handle the bitrate.

What I want to do is set the maximum bitrate, which can be done, I think.  I fired up gconf-editor and went to /system/gstreamer/audio/profiles/cdlossy and changed the pipeline to: rawvorbisenc name=enc max-bitrate=250000 quality=0.6.  gst-inspect-0.8 rawvorbisenc suggests that this should work.

Problem is, when I use Sound Juicer now, I receive the following error when trying to rip: Could not create GStreamer encoder ((null)).  I mostly found out about rawvorbisenc from #gstreamer on Freenode but they were unable to help with this error.

Anybody have any suggestions?  I'd like to stick with Sound Juicer as it otherwise does everything I need.  Thanks very much.

---

### Post by vaskark on 2005-04-05
I can't help with this one, but I'd like to thank you for pointing out how to change the encoding rate. I've been looking for an answer to that for awhile!

---

