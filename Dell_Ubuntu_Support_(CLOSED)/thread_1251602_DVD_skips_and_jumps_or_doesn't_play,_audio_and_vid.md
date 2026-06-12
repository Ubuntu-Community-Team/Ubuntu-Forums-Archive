---
title: "DVD skips and jumps or doesn't play, audio and video"
date: 2009-08-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kordite on 2009-08-27
I just received my Dell Inspiron 1545 with Ubuntu 8 preinstalled. Although I can get the Dell PowerDVD to play, there are several things I don't like about it (locked regions, frame stepping, haven't figured out full screen) so I have installed VLC and Ogle. They have difficulty with playback.

VLC will open a window for a moment and then have that window disappear. The sound will drop in and out and eventually the window comes back and the video barely plays. A moment of video, hangs for 5 seconds, another moment of motion, etc.

Ogle will play bursts of sound. The window will be completely blank. Eventually, I doesn't seem to do anything.

The Totem window goes black and white and then "not responding."

When I first installed these, they would just close. I could launch the applications but once I tried to open the DVD the application would just close. To get what I have now, I had to accept Dell PowerDVD's demand that I change the drive's region from Free to 1.

Based on previous forum topics, I've installed vlc-plugin-esd, mozilla-plugin-vlc and libdvdcss2 not no apparent improvement. It's probably a codec thing that I'm missing and would like some guidance.

---

### Post by Gausian on 2009-08-28
did you install libdvdcss2 from the Medibuntu repository? or somewhere else?

have you installed ubuntu-restriced-extras from the multiverse repo?

---

### Post by kordite on 2009-08-28
I did all this several days ago so I didn't remember where exactly I had read the instructions that I followed so, based on your questions, I went searching from the beginning and started over. 

It seems to have worked.

I may have done something wrong the first time or simply not been paying attention to errors. In any case, I feel like a dolt. 

I work at a help desk. I should know better.

---

