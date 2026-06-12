---
title: "Nautilus Problem??"
date: 2006-09-14
forum: Desktop Environments
---

### Post by nevle on 2006-09-14
After upgrading to Dapper I can no longer play mp3s by clicking on them in nautilus, error message says "cant open its mp3 document..." they will only play if i "open with.." how do i fix this? (nautilus is setup to play executables)

---

### Post by Leonivek on 2006-09-14
I did a post on my blog about File Associations... See [http://linuxfud.wordpress.com/2006/09/03/ubuntu-linux-file-associations/](http://linuxfud.wordpress.com/2006/09/03/ubuntu-linux-file-associations/)

Hope that helps!

---

### Post by nevle on 2006-09-14
My file associations are set to open with xmms, the error message says the file is "mp3 document file" yet file info says its "mp3 audio" it doesnt matter what player i use they wont open automatically,file perissions are rwxr-x-r-x.this happens for all my mp3s, had no problem in 5.10:confused:

---

### Post by nevle on 2006-09-14
ps i have rox-filer on my system, double click auto opens file with xmms as its supposed to ????

---

### Post by nevle on 2006-09-15
pps.removing mp3 extention and it plays, replacing mp3 extention and it still works.the file will only play correctly if i go through these 2 steps

---

### Post by nevle on 2006-09-15
i think i'll just get drunk and convert all my so-called mp3's to ogg..ogg works. or not use nautilus. aaaaaahh!

---

### Post by Leonivek on 2006-09-15
Now that I think of it, I read somewhere in this forum about issues with MP3s with uppercase extension and lower case extension... One of them won't open, or something like that... Maybe that's what it is.  Try different cases...

---

### Post by canadianwriterman on 2006-09-15
The other thing that it could be, nevle, is that it's a bit confusing to set "Open With" in Nautilus. When you right click on an MP3 file, you see an "Open With" option. But, that is only for one use. To _permanently_ set "Open With," click on "Properties" and then the "open With" tab and set the player. Just a suggestion.

---

### Post by nevle on 2006-09-16
Tried to change mp3 to MP3 but didn't make any difference,however if i open system tools>Configuration Editor>system>gstreamer>0.10>audio>global mp3 doesn't appear in the list but it does appear in gstreamer>0.8>audio>global which worked properly. What have i done wrong? i need to add ..... 
ps. removing the mp3 extension works.

---

