---
title: "Wine crashes whole computer"
date: 2006-08-02
forum: Desktop Environments
---

### Post by dmb on 2006-08-02
For some reason, I have not been having a good time with wine and my e1705 laptop. It uses the nvidia driver. Anyway, when i run some things on wine, it will just freeze the whole computer, no mouse, killing X by hitting crtl-alt-bkspc, and changing to an alternite terminal. Anyone know what the culprit could be? A direct example of a crash it using winetools and running the IE6 installer, it crashes the whole computer every time.

---

### Post by fourchannel on 2006-08-02
I dunno from your description alone but try this...```
strace wine file.exe
``` and paste the output in {code} tags, cause it will be a lot of output. Maybe we can see what is causing the fault.

*subtlely coughs*
It *is* trying to run IE afterall. =D

---

### Post by dmb on 2006-08-02
I don't think this is going to work, as it freezes when I do that, but ill redirect the output to a file and see if that helps.

---

