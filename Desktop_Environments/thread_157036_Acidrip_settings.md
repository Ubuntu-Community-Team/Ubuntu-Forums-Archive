---
title: "Acidrip settings"
date: 2006-04-08
forum: Desktop Environments
---

### Post by deepsiks on 2006-04-08
I just started using acidrip.  First, not knowing anything about ripping on linux, I had video set to one pass.  Needless to say, the quality of the avi was poop.  Then I shifted it to use xvid with 3 passes and video does seem quite good.  Now the only problem is the audio laggs the video.  Can someone please post what the best settings are and how to overcome the lagging audio problem.
Thanks

---

### Post by veratyr on 2006-04-12
I usually do a 2 pass xvid using cbr mp3. Fore example:

```
mencoder dvd://1 -dvd-device /dev/dvd  -alang English   -info srcform="DVD ripped by acidrip.sf.net" -oac mp3lame -lameopts cbr:br=128  -ovc xvid -xvidencopts bitrate=1116:pass=1 -vf lavcdeint,crop=704:480:8:0,scale=640:480    -o "/dev/null"

mencoder dvd://1 -dvd-device /dev/dvd  -alang English   -info srcform="DVD ripped by acidrip.sf.net" -oac mp3lame -lameopts cbr:br=128  -ovc xvid -xvidencopts bitrate=1116:pass=2 -vf lavcdeint,crop=704:480:8:0,scale=640:480    -o "/home/mike/blah.avi"
```

I've never had a problem with audio skipping or getting out-of-sync when using acidrip. Maybe DMA isn't enabled for your dvd drive? Just a guess.

---

