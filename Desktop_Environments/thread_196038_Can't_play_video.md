---
title: "Can't play video"
date: 2006-06-13
forum: Desktop Environments
---

### Post by codypumper on 2006-06-13
No matter what movie player I use (vlc, mplayer, real, etc.) and what type of movie file I play the media player appears then closes. It just flashes. Does anyone have a clue of whats going on?

---

### Post by codypumper on 2006-06-13
sorry, it only happens with .mov and .avi files.

---

### Post by taurus on 2006-06-13
Have you installed win32 codecs on your machine?
```

sudo apt-get install w32codecs

```

---

### Post by codypumper on 2006-06-13
yes I have. I just reinstalled mplayer, and restarted the computer, and they will work on mplayer but nothing else now...

---

### Post by beefcurry on 2007-03-09
found a solution for this yet because i am having the exact same problem

---

### Post by codypumper on 2007-03-09
I sort of found a solution. My sound card was having problems, and I had to mess with alsa for a long time.

---

### Post by beefcurry on 2007-03-10
for me it seemed to be a conflict with Firefox, had to shut firefox before it worked. Seems like this one problem could have multiple causes.

---

