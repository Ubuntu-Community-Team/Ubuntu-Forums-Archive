---
title: "FFMPEG + Floola?"
date: 2007-10-04
forum: Desktop Environments
---

### Post by Quiane on 2007-10-04
how do i get ffmpeg to work with floola?? I try the conversion tool floola comes with and it just closes the box and goes back to the add files window.
I'm running feisty fawn...any help would be greatly appreciated!!!

---

### Post by Duroon on 2008-01-03
I have the same problem currently. I had everything working under Floola 2.2 but as soon as I upgraded to version 2.3 of Floola the video conversion stopped working. The best I can determine is that ffmpeg isn't working as Floola expects it to. Anyone solved this problem yet?

---

### Post by Floola on 2008-01-04
Recently there's been an update of ffmpeg package in the repositories, this might have overwritten your working ffmpeg binary. Nothing changed in the code from 2.2 to 2.4.

You need to rebuild ffmpeg from sources as described here:

[http://ubuntuforums.org/showthread.php?t=114946](http://ubuntuforums.org/showthread.php?t=114946) (see installing ffmpeg with x264)

HTH,
Tomas

---

### Post by Duroon on 2008-01-04
Thanks! That did the trick perfectly. I am back to converting videos for my ipod!

---

### Post by somethingsin on 2008-03-20
that guide doesn't seem to work...
when I configure it, it gives me unknown option errors for quite a few options

---

