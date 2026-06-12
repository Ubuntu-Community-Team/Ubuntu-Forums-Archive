---
title: "Converting from wmv/avi/mpg to mp4/3gp"
date: 2006-03-03
forum: Desktop Environments
---

### Post by xmastree on 2006-03-03
All I waht to do is convert some funny short videos to a format compatible with my phone. Not a lot to ask really, is it? :???: 

I tried this:
[http://ubuntuforums.org/showthread.php?t=114946](http://ubuntuforums.org/showthread.php?t=114946)
but that didn't work at all for me. I tried the 'modified' ffmpeg in [this](http://ubuntuforums.org/showpost.php?p=787795&postcount=139) post but that wouldn't work either.

Is there any other way to convert them? preferably a command line program so I can just use a nautilus script.

Transferring to the phone itself is not a problem, i just need to convert the video.

---

### Post by rootkit on 2008-01-31
have a look: [http://ubuntuforums.org/showthread.php?t=684197](http://ubuntuforums.org/showthread.php?t=684197)

---

### Post by harold4 on 2008-01-31
Either replace $1 with the input/output file, or toss this in your $PATH
```

!/bin/bash
ffmpeg -i $1 -f mp4 -acodec mp2 `pwd`/$1.mp4

```

---

