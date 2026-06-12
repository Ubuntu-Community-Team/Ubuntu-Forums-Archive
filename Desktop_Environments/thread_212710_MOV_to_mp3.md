---
title: "MOV to mp3?"
date: 2006-07-10
forum: Desktop Environments
---

### Post by Mike_N on 2006-07-10
So... iTunes used to let you convert MOVs to audio but no longer, only iPod Video conversion is on their. So... can i use any app on Ubuntu to get the audio out?

Thanks, Mike

---

### Post by Paerez on 2006-07-10
hmmm, ffmpeg will probably work but I don't know exactly the commands to run it. If you're really lucky this will work:
```
# ffmpeg -i infile.mov outaudio.mp3
```
replace "infile.mov" with your mov file and outaudio with the name that you want to use.

---

