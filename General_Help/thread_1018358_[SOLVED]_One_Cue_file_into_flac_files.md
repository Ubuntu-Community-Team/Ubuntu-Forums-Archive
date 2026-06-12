---
title: "[SOLVED] One Cue file into flac files"
date: 2008-12-22
forum: General Help
---

### Post by Bloemetjesgordijn on 2008-12-22
Hi,

I have several CUE files, how do I seperate them into multiples seperate flac files.

I hav googled but found nowere a newby solution.


Cheerz

Bloemetjesgordijn

---

### Post by eBoxNet on 2008-12-22
try this tutorial it may help you...
[http://stillstup.blogspot.com/2008/07/split-lossless-audio-ape-flac-wv-wav-by.html](http://stillstup.blogspot.com/2008/07/split-lossless-audio-ape-flac-wv-wav-by.html)

---

### Post by Bloemetjesgordijn on 2008-12-22
> **eBoxNet said:**
> try this tutorial it may help you...
[http://stillstup.blogspot.com/2008/07/split-lossless-audio-ape-flac-wv-wav-by.html](http://stillstup.blogspot.com/2008/07/split-lossless-audio-ape-flac-wv-wav-by.html)


Thx man


I will give it a go.

Cheerz 
Bloemetjesgordijn

---

### Post by vanadium on 2008-12-22
It can be even simpler nowadays.

```

shntool split file.flac -f file.cue -o flac

```

If you add the option " -t '%n - %t'", your output files will automatically be named by "tracknumber - title".

For transferring tags, you still need to rely on cuetools, though.

---

