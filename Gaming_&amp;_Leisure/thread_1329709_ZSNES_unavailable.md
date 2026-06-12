---
title: "ZSNES unavailable?"
date: 2009-11-17
forum: Gaming &amp; Leisure
---

### Post by Cam! on 2009-11-17
In the Ubuntu Software Center, I'm unable to download + install ZSNES. Any links to a working copy?

---

### Post by jpmelos on 2009-11-17
You marked the post as [SOLVED], can you post the solution, please? Thanks! :D

---

### Post by Cam! on 2009-11-17
OH! I feel so dumb. -_-

---

### Post by jpmelos on 2009-11-18
So it's not solved?

---

### Post by KIAaze on 2009-11-19
zsnes is not available for 64bit architectures. This might be your problem.

Here's what worked for me:

1) Downloaded and installed the intrepid 64bit version of zsnes: [http://packages.ubuntu.com/intrepid-updates/zsnes](http://packages.ubuntu.com/intrepid-updates/zsnes)
2) Launched zsnes with
```
zsnes -ad sdl
```
to avoid segfault.

cf also: [http://ubuntuforums.org/showthread.php?t=588744](http://ubuntuforums.org/showthread.php?t=588744)

---

