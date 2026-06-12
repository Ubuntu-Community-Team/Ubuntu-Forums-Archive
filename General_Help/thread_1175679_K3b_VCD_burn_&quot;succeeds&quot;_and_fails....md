---
title: "K3b VCD burn &quot;succeeds&quot; and fails..."
date: 2009-06-01
forum: General Help
---

### Post by t0p on 2009-06-01
I've got some flash video files that I'd like to play on a DVD-Video player.  Unfortunately my optical drive can write to CDs but can only read DVDs, so I figured I'd write the files to VCD.

From the **ffmpeg** man page I got the following command:

```
ffmpeg -i file.flv -target pal-vcd file.mpg
```

(I live in the UK, so PAL is the format I need to use.)

Okay, so I used ffmpeg to convert a .flv file to VCD format, then used K3b to write it to a CD-R.  K3b reported "success".  But the resulting disc won't mount on my computer, and a DVD-Video player that supports VCD reports the disc as "Unknown Disc".

Can anyone tell me where I've gone wrong?  And what I need to do to get it right?

---

