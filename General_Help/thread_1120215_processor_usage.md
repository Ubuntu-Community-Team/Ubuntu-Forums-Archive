---
title: "processor usage"
date: 2009-04-08
forum: General Help
---

### Post by slade on 2009-04-08
any idea what's going on here?  Xorg is hogging...  well, more processor power than my computer technically has, by definition.

[http://img511.imageshack.us/img511/5495/screenshot12x.png](http://img511.imageshack.us/img511/5495/screenshot12x.png)

---

### Post by benj1 on 2009-04-08
sorry can't help.
im impressed that you managed to more than double your processor speed though, now thats overclocking :p

---

### Post by Yashiro on 2009-04-08
And if you kill Firefox and the operawrapper process?

---

### Post by slade on 2009-04-08
killing firefox alone fixed the problem - linux doesn't seem to like it when i have 96 tabs open and leave my computer on for a few days.  any idea *why* that happens, though?  it's happened to me on fedora too.  Xorg suddenly maxes out the processor when I'm using my computer heavily.

the thing is I'm *not* overclocking, top apparently bugged out for some reason and showed a CPU usage that high.

---

### Post by FrostDust on 2009-04-08
As for the why, it could be the tabs you have open in the background in Firefox are using CPU power for stuff like Javascript, I notice my processor usage spikes when I open up Facebook. Maybe just close tabs of similar style when you aren't using them.

Also, I noticed your CPUs are operating in mirror of each other. When one is at 100%, the other drops to zero. This indicates that, like you said, it's Firefox that is using your CPU. I surmise it isn't coded for multiple CPUs, so it can't split up the whole program across the two you have, but instead maxes out one at a time.

The times where the lines crossed (one CPU went to full usage, the other went to half), did that correspond with you doing anything in Firefox, like opening a new tab or clicking on a link? Also, if Firefox is maxing one out, I'd be guessing you can open up a new program, and see it start to use the unused CPU.

---

### Post by slade on 2009-04-08
no, i think the usage would switch between processors just to not keep one at 100% and the other at 20% all the time, so both processors get even usage.

i'm wondering more 1) why is that much of the CPU suddenly being used, that shouldn't happen even with that many tabs 2) why Xorg is shown as the process using the CPU, when firefox is the problem 3) why the usage spikes over 200%, which isn't exactly possible and 4) why top shows this, while system monitor only shows about 20% cpu usage under processes.

---

### Post by Yashiro on 2009-04-08
Xorg is shown because it's a video sub process doing it.
It was probably Flash bugging out as usual.

---

