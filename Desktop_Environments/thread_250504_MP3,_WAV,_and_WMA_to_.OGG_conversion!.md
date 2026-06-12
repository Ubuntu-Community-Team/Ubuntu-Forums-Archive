---
title: "MP3, WAV, and WMA to .OGG conversion!?"
date: 2006-09-04
forum: Desktop Environments
---

### Post by sisonpyh on 2006-09-04
Is there a little program (tool) for Ubuntu or GNU/Linux in general to convert MP3, WAV, and WMA to .OGG files perhaps? The reason I'd like to do this is that compression with .OGG is better and I lose no sound quality at all. In fact I believe .OGG quality is actually better than MP3. Moreover, I have about 17499 songs and it takes up almost 72GB HDD space, so better compression might help me save some disk space too...

Any help would be greatly appreciated :rolleyes:

---

### Post by Spookster on 2006-09-04
Assuming you're comfortable using the command line...

sox - a great program for converting file formats, can convert from mp3 and wav to ogg (not sure about wma). 
```
apt-get install sox
```

oggenc - encodes WAV files to ogg format with lots of flexibility. 
```
apt-get install vorbis-tools
```

There is always a loss of quality in converting from one lossy format to another though.

---

### Post by arkangel on 2006-09-04
you can also do it  with one nautilus script , that means  select the file  and righ click...
check here 

[http://ubuntuforums.org/showthread.php?t=249832](http://ubuntuforums.org/showthread.php?t=249832)

---

### Post by sisonpyh on 2006-09-06
Thanks for all the help, I'll be looking into it!

---

