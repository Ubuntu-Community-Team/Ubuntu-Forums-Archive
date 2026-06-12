---
title: "Samsung YP-S3 mp3 player works, now how about video."
date: 2009-03-18
forum: General Help
---

### Post by randomas on 2009-03-18
I just bought one of these great little players which support OGG music files (even if this feature is not advertised), and got it working in hardy following [this here how-to]("http://ubuntuforums.org/showthread.php?t=651894"). 

So now mtp transfer is sorted I'd like to get some videos on this thing and so far I haven't had any luck. I tried both the jSVIcoder application and the settings in the how-to (changing a few numbers), but havn't managed to get it working. 

the mplayer info for one of the loaded .svi files is ```
VIDEO: [XVID] 208x176 24bpp 15.000 fps 341.2 kbps (41.6 kbyte/s) 
Clip info: 
Software: SSGP 
```

and my mencoder.conf reads ```
[svi]
fps=15
srate=44100
mc=0.1
oac=mp3lame=true
lameopts=cbr=true:br=320
ovc=xvid=true
xvidencopts=fixed_quant=4:max_bframes=0:quant_type=h263
profile-desc="fps=15 srate=44100 mc=0.1 oac=mp3lame=true lameopts=cbr=true:br=128 ovc=xvid=true xvidencopts=fixed_quant=4:max_bframes=0:quant_type=h263"

```

I tried using the following command:```
 mencoder input.avi -o output.svi -profile svi -vf scale=208:176,harddup
```

Any help would be much appreciated.

TIA

---

### Post by knowmad on 2009-12-26
Thanks for sharing your work. I've tried using your info as well as others from around here and the web to no avail. Have you ever had any luck getting videos loaded onto the S3 from Linux?

---

### Post by randomas on 2010-01-05
In the end I gave up, but having tried and failed in windows as was was quite consolatory. 

If you manage let us know!

---

