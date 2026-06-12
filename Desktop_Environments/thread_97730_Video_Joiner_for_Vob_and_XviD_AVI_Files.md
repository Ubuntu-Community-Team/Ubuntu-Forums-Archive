---
title: "Video Joiner for Vob and XviD AVI Files"
date: 2005-12-01
forum: Desktop Environments
---

### Post by sinbad782 on 2005-12-01
I've been transcoding some video from DVDs and was wondering if there is a good program for joining the resulting AVI files. The files are all encoded in XviD format, with MP3 soundtracks. 

The same goes for some DVD rips that I have - how does one join Vob files together (would make transcoding simpler). If this is as simple as just using the cat function at the command line then please let me know!

Thanks, PJS

---

### Post by siucdude on 2006-01-01
has anyone found anything on this.

---

### Post by goombah88 on 2006-02-21
[QUOTE=sinbad782]I've been transcoding some video from DVDs and was wondering if there is a good program for joining the resulting AVI files. The files are all encoded in XviD format, with MP3 soundtracks. 

The same goes for some DVD rips that I have - how does one join Vob files together (would make transcoding simpler). If this is as simple as just using the cat function at the command line then please let me know!

Thanks, PJS[/QUOTE]

sinbad782,  i just finished joining 2 XVID movies using avidemux-2.1.0.  open the first file, then Append the other movies in the order you want them joined.  i installed avidemux using automatix, if that helps.

---

### Post by taurus on 2006-02-21
Or

sudo apt-get install avimerge
avimerge -o filename.avi -i first_file.avi second_file.avi

---

