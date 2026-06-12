---
title: "NetPanzer Segmentation Fault"
date: 2006-01-21
forum: Gaming &amp; Leisure
---

### Post by TheIdiotThatIsMe on 2006-01-21
First of all: Anyone who says there are no good games for linux has obviously never played this one! Awesome game :) 

Unfortunately, as I play it, I get random crashes, with the following output in the terminal:

```
Received signal SIGSEGV(11)
aborting and trying to shutdown.
Segmentation fault
```

The first time I played it I played for over an hour before it crashed, the second time only took five minutes. Very frustrating, to say the least. Any ideas?

---

### Post by amohanty on 2006-01-21
> Received signal SIGSEGV(11)
aborting and trying to shutdown.
Segmentation fault

Welcome to the world of C/CPP binaries :) Look for a file called **core** or **dump** or something to that effect in the directory from where you started the app. Then send and email to the developer with the core dump file and an exact (as far as possible) description of what you were doing when it crashed. Hopefully he/she/they will be able to figure out where the bug is.

HTH
AM

---

