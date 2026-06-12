---
title: "Zsnes and pSX not working!"
date: 2008-11-07
forum: Gaming &amp; Leisure
---

### Post by rick08 on 2008-11-07
I recently upgraded to 8.10 a day before it's release and I just decided now would be a great time to play some playstation or super nintendo games. I tried to open zsnes and nothing at all happens. I tried to open Psx and it just flashes and thats all I see of it. I looked in the zsnes folder to see if the link was bad, but I found only the zsnes config files and thats all. I hope all I need to do is reinstall the program. If anyone can help me fix these two emulator that would really be great. I'm getting tired of OpenArena since i've been playing it for 5 hours straight lol.

---

### Post by Grishka on 2008-11-07
you'll have to run them from the terminal, and post the output. also, are you on a 64-bit sytem?

---

### Post by rick08 on 2008-11-07
I am not on a 64bit system.  I found out why zsnes won't work, but I am still looking for an answer for pSX's failure.  When I try to run pSX from terminal it says command not found.

---

### Post by rick08 on 2008-11-07
sorry here is pSX's output.
```
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
Segmentation fault
```

---

### Post by dfreer on 2008-11-07
See if this package or the script (whichever you feel like using) fixes pSX for you:
[http://ubuntuforums.org/showpost.php?p=6127662&postcount=246](http://ubuntuforums.org/showpost.php?p=6127662&postcount=246)

Basically, for ZSNES you need to grab a binary NOT compiled under GCC 4.3.2 (Ubuntu Intrepid), preferably ZSNES 1.51b. For pSX, you need to kill pulseaudio before you run pSX, due to a conflict with pulseaudio.

---

### Post by Grishka on 2008-11-07
> **rick08 said:**
> sorry here is pSX's output.
```
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
Segmentation fault
```

'killall pulseaudio' should fix this.

---

