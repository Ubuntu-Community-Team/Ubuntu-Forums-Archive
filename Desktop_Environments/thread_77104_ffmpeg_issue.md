---
title: "ffmpeg issue"
date: 2005-10-16
forum: Desktop Environments
---

### Post by dc2447 on 2005-10-16
Hi I am converting mpeg2 files using ffmpeg, this is the argument I'm passing:

> ffmpeg -i mympeg.mpg -y -f vcd -vcodec mpeg1video -map 0.0:0.0 -b 1150 -s 352x240 -r 29.97 -g 12 -qmin 3 -qmax 13 -hq -acodec mp2 -ab 224 -ar 44100 -ac 2 -map 0.1:0.1 -t mytitle output.mpg

The problem is that when viewing the mpegs using gxine I don't get any information on the length of the clip.  Anybody know why?

---

