---
title: "webcam software search."
date: 2006-07-14
forum: Desktop Environments
---

### Post by ephman on 2006-07-14
hi,

i'm searching for some software that i can use to record sound and video with my webcam.  any suggestions?

thanks,
ephman

---

### Post by ephman on 2006-07-15
bump

---

### Post by grizzly on 2006-07-16
bump from here too, looking for a simple app to record video from my webcam! 
Tried camstream , but camorama , both can take pics , but none can record videos.

---

### Post by reclusivemonkey on 2006-07-16
Try "streamer"; its in the Graphics (Universe) repository.

```
DESCRIPTION
       streamer  reads  audio  and/or video data from /dev/video0 and /dev/dsp
       and writes the data to the disk.  Various output formats are supported.
       Start  streamer  with  ’-h’  for a list of options and supported output
       formats.

       streamer will use the file extention of the output file name to  figure
       which  format to use.  You need the -f/-F options only if the extention
       allows more than one format.  If you get the "neither audio  nor  video
       format  specified/found" message and don’t know why, you can enable the
       debug output (-d switch) to see what is going on.

       You can safely stop the recording at any time  with  Ctrl+C.   streamer
       will  catch  the  signal and stop recording correctly (i.e. write movie
       file headers) before exiting.
```

---

