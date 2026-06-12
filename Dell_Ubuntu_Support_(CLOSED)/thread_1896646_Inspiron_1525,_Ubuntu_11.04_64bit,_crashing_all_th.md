---
title: "Inspiron 1525, Ubuntu 11.04 64bit, crashing all the time"
date: 2011-12-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by teyesahr on 2011-12-17
My Dell Inspiron 1525 is crashing all the time, now, and I have no clue why. At first I thought it was overheating and shutting down to avoid permanent damage to the CPU, but it's doing it at times when that wouldn't make sense. I'm not even sure how to troubleshoot. Any help?

As the title indicates, I'm running Ubuntu 11.04 64bit. I have 4GB memory. I can get any information I need... if you tell me what I need. Thanks!

---

### Post by mikewhatever on 2011-12-20
What do you mean by 'crashing'? Seriously, can you describe exactly what happens without vague terms.

Is Lubuntu the only OS or do you have Windows installed as well? If so, does it do any kind of 'crashing'.

---

### Post by teyesahr on 2011-12-20
It just shuts down without warning. I might be watching a video online (hulu, Daily Show, whatever), or just working on some spreadsheets, and the whole computer turns off.

It will turn back on without problems, although occasionally it has shut down again a few minutes later.

The only OS I have installed is Ubuntu 11.04 64bit. I do have Windows 7 Ultimate as a guest via VirtualBox.

---

### Post by mikewhatever on 2011-12-20
Thanks for the clarification. It could be a bug, or a hardware problem. I'd run Memtest to check the RAM, and look through the logs for errors.

---

### Post by teyesahr on 2011-12-20
Thanks for the advice. I'll run Memtest and post the results.

Which logs in particular should I look at? When I run Log File Viewer, there are literally dozens and it's not obvious where to begin.

---

### Post by mikewhatever on 2011-12-20
Try looking at the following: syslog, kern.log, Xorg. Logs are often rotated on restart, so it would make sense to check the old ones: syslog.1, kern.log.1, Xorg.0.log.old.

---

### Post by teyesahr on 2011-12-21
O...k.... Just found this in syslog:

```
Dec 21 20:17:18 linden kernel: [ 2549.154320] CPU1: Core temperature above threshold, cpu clock throttled (total events = 1)
Dec 21 20:17:18 linden kernel: [ 2549.154966] CPU1: Core temperature/speed normal
Dec 21 20:19:27 linden kernel: [ 2678.188911] Critical temperature reached (99 C), shutting down.
```

Safe to assume my laptop is overheating (near-boiling?!). Now: why? It's three years old and this has never happened before. New fan? Other ideas?

---

