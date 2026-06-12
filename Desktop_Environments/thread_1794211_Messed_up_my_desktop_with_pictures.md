---
title: "Messed up my desktop with pictures"
date: 2011-06-30
forum: Desktop Environments
---

### Post by pankajgarg on 2011-06-30
I actually wanted to extract pictures from a video and used the command:


ffmpeg -i Video.mpg Pictures%d.jpg
as mentioned at 
[http://ubuntuforums.org/showthread.php?t=1141293](http://ubuntuforums.org/showthread.php?t=1141293)

but my desktop is not responding now and even the terminal is working very very slow. 

I tried to move the contents to other folder but the terminal is not working. The memory usage has risen from the normal 23% on my laptop to 89% [I have a 1 GB RAM].

---

### Post by ajgreeny on 2011-06-30
How big and long was the video, because if you have a separate jpg for each frame of a long video, you may have filled a lot of space.

However if the system is still processing the video, it may simply be that there is a lot of resource hungry decoding and re-encoding going on.  In a new terminal try ```
top
```to see if ffmpeg is using all your cpu%.

---

### Post by jerrrys on 2011-06-30
i only do it with home movies, but i use "videocut".  i find it fast, at least on home movies...

---

### Post by pankajgarg on 2011-06-30
well the video was of around 700 MB and it made  around 25000 pictures on the desktop. but my command of moving it worked and i deleted the pictures from there.

and now i used the command again by setting the number of frames per second. But the quality of the pictures retrieved is not very good. can do something for it?


Is there any particular software available for this kind of processing available?

---

