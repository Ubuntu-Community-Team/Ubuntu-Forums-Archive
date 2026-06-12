---
title: "Help with archiving."
date: 2009-03-01
forum: General Help
---

### Post by BDH1977 on 2009-03-01
I need help with some .rar files I just switched to Ubuntu a few days ago and I don't know it that well yet. I used to use winrar with XP and it would recognise all the files as one and would then extract them when I would click on .r00. I tried to use archive manager but it does not recognise the file. What program would I use to un archive these files?

---

### Post by Simian Man on 2009-03-01
I remember installing unrar from the repos when someone sent me a rar archive.  It is a command line application.  Use it like 'unrar file.rar'.

---

### Post by oldos2er on 2009-03-01
Run
```
sudo apt-get update && sudo apt-get install rar unrar
```
in a terminal, then try the archive manager again.

---

### Post by BDH1977 on 2009-03-01
> **oldos2er said:**
> Run
```
sudo apt-get update && sudo apt-get install rar unrar
```
in a terminal, then try the archive manager again.

Thank you so much. It worked. this is my first thread here but I have been reading this forum for a while now and it has helped me switch to ubuntu without much problems.

---

