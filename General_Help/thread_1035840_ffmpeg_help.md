---
title: "ffmpeg help"
date: 2009-01-10
forum: General Help
---

### Post by romeyde on 2009-01-10
I have a cronjob that runs nightly and coverts captured TV shows off the usb tuner from m2t to mp4.   This reduces an hour show from 8 gig to about 700 meg.   It takes about 50 minutes for a one hour show.   The resulting quality is OK but a little blocky.   Any suggestions as to what I can do to this line to get maybe a little more quality without dramatically increasing the conversion time?

/usr/bin/ffmpeg -i $filename -y -vcodec libx264 -acodec libfaac -f mp4 -mbd rd -flags 4mv+trell+aic+qprd+mv0 -coder 0 -me_method epzs -subq 0 -sc_threshold -1 -cmp 2 -subcmp 2 -flags2 dct8x8+skiprd -level 41 -bf 3 -ac 2 -ab 128 -threads 3 -s hd720 ${inputdir}/${basename}-${date}.mp4

---

### Post by FakeOutdoorsman on 2009-01-10
You're not declaring the bitrate, so ffmpeg will use the default of 200 kb/s.  You can get much better quality by using a recent version of x264 and ffmpeg with the libx264 presets:

[HOWTO: Compile the latest ffmpeg and x264 from source](http://ubuntuforums.org/showthread.php?t=786095)

Since you are more concerned with speed than a target bitrate, then I recommend using one-pass CRF mode with the presets mentioned in the guide linked above:
```
ffmpeg -i input.avi -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre default -crf 26 -threads 0 output.mp4
```
This will probably take twice as long as your command, but it will look much nicer and probably be a smaller file size.

If you want something faster:
```
ffmpeg -i input.avi -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre fastfirstpass -crf 26 -threads 0 output.mp4
```
It's not optimal, but it will probably still look nicer and I estimate it will be 1/3 slower than your original command.

---

### Post by romeyde on 2009-01-11
Thanks, I'll give both of those a try.   I actually did already attempt to manually update libx264 but it looks like maybe it's still pointing to the older version.  Found to on my box:

lrwxrwxrwx 1 root root 13 2009-01-09 13:04 /usr/lib/libx264.so -> libx264.so.59
lrwxrwxrwx 1 root root 13 2009-01-09 13:29 /usr/local/lib/libx264.so -> libx264.so.65

---------

Thanks, followed that guide and it was more complete than the others I was working off of.   Included some additional steps that I think resolved my issue.   Purged the older versions, locked my new compiled package and testing both of your suggested methods now.

Thanks for the input.

---

### Post by romeyde on 2009-01-12
Compiled new version of ffmpeg and tried both examples you suggested and in both cases, my sound now gets completely out of sync where as it worked fine with the older version.   Unfortunately, my commands no longer work with the newer ffmpeg, I get an invalid -flag option.   Any ideas.

This is the original that worked and I'm just looking for ideas to improve it.   These are going to be viewed on a PS3.

/usr/local/bin/ffmpeg -i ./input.m2t -y -vcodec libx264 -acodec libfaac -f mp4 -mbd rd -flags 4mv+trell+aic+qprd+mv0 -coder 0 -me_method epzs -subq 0 -sc_threshold -1 -cmp 2 -subcmp 2 -flags2 dct8x8+skiprd -level 41 -bf 3 -ac 2 -ab 128 -threads 3 -s hd720 ./output.mp4

tried

/usr/local/bin/ffmpeg -i ./output.m2t -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre default -crf 26 -threads 3 ./EverbodyHatesChris-20090109-200000-3.mp4

and 

/usr/local/bin/ffmpeg -i ./input.m2t -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre fastfirstpass -crf 26 -s hd720 -threads 3 ./output.mp4

---

### Post by FakeOutdoorsman on 2009-01-12
Here is a modified version of your original command which should work for a recent ffmpeg:
```
ffmpeg -i input.avi -vcodec libx264 -acodec libfaac -f mp4 -mbd rd -flags 4mv+aic+qprd+mv0 -trellis 1 -coder 0 -me_method epzs -subq 1 -sc_threshold -1 -cmp 2 -subcmp 2 -flags2 dct8x8+skiprd -level 41 -bf 3 -ac 2 -ab 128k -threads 0 out.mp4
```
If you want to encode just a certain number of frames for testing then use the "-vframes" option: -vframes 300 will encode the first 300 frames.

---

### Post by romeyde on 2009-01-12
thanks, that works but the audio still goes out of sync about 10 mins into the video.   keep playing with the options but not finding a combination that works.  will keep messing, don't want to have to fall back to the old ffmpeg.

---

