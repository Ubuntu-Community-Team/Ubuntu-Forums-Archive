---
title: "What is the command for hardware/process status?"
date: 2006-09-17
forum: Desktop Environments
---

### Post by kuririkura on 2006-09-17
What is the command for hardware/process status?
So i can get information from ubuntu like what i get in windows task manager, such as: memory use, proccessor utilization, hown much a process consume memory... etc,

Thx

Regards,
Eka

---

### Post by codejunkie on 2006-09-17
> **kuririkura said:**
> What is the command for hardware/process status?
So i can get information from ubuntu like what i get in windows task manager, such as: memory use, proccessor utilization, hown much a process consume memory... etc,

Thx

Regards,
Eka
open a terminal and enter ```
top
```or you can click on System/Administration/System Monitor

---

### Post by snakyjake on 2006-09-26
Also try **Process Status**:

```
ps -l
```
or for other options, read the help:
```
ps --help
```

or the Linux MAN Pages Online for [Process Status]("http://man.he.net/?topic=ps&section=all")

Jake

P.S. I usually prefer the command line because the command line always works, and it works the same regardless of window manager/desktop environment or distribution.

---

