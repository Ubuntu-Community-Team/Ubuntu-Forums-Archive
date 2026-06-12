---
title: "Merging files"
date: 2008-09-05
forum: Desktop Environments
---

### Post by Firm18 on 2008-09-05
Ok, I'm really anoyed with this stupid merging files. How do I do that? How can I put two files together (sth sth.avi.001 and sth sth.avi.002) to make them run. I used gnome commander and I didn't know how it works, then I used "cat" in terminal but it didn't do anything either.

CHeers....

---

### Post by benerivo on 2008-09-05
I know mencoder can work. I have used this command ```
mencoder -oac copy -ovc copy -o '/media/newvideo.mpg' '/media/test1.mp4' '/media/test/2.mp4'
```
where the first file is the output and test 1 and 2 are the input files, and the commands before the file names are telling it to make a direct copy of the video and audio. I think this only works when the two input files have the same codec, resolution etc.. When they differ, then you have to specify what format/codec you want the resulting file to be in. This command might work```
mencoder -oac mp3lame -ovc raw -o '/media/1.mpg' '/media/test/1.mp4' '/media/test/2.mp4'
```

---

