---
title: "Running out of memory"
date: 2008-12-23
forum: General Help
---

### Post by kulkarniniraj on 2008-12-23
Hi
I am using Ubuntu hardy 64.
I am having intel core 2 duo & 512 MB ram

I have upgraded recently from gutsy to hardy.
now I have noticed that my memory usage is around 450 MB (90-92%)

Tell me if this is normal, since it is creating a problem in smooth running of applications.

If not how can i reduce usage? Which are unnecessary processes eating up memory? Please help.

---

### Post by hyper_ch on 2008-12-23
run:
```

free -m

```
and post that here.

---

### Post by scorp123 on 2008-12-23
> **kulkarniniraj said:**
> now I have noticed that my memory usage is around 450 MB (90-92%) And how precisely did you notice that? Chances are a lot of that "used" memory is actually for buffering and caching.

Please do as "hyper_CH" says and post here the output he requested.

---

### Post by wfp on 2008-12-23
These are some things i did to free up some memory. System>preferences>sessions. I unchecked bluetooth manager> i do not need it.2.Evolution alarm notifier- I do not use it i use thunderbird.3. Print que applet- i do not have a printer hooked up.4,5 Tracker and tracker applet unchecked both of these.6, visual assistance i do not use it. leave desktop effects off.

---

### Post by kulkarniniraj on 2008-12-23
total       used       free     shared    buffers     cached
Mem:           491        485          6          0          5         93
-/+ buffers/cache:        387        104
Swap:         1027        147        880


Also htop shows one of my CPU usage is 100%
please help.

---

