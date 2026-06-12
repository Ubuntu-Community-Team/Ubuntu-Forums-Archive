---
title: "Installing snap changes sound volume"
date: 2023-08-24
forum: Desktop Environments
---

### Post by fefniir2 on 2023-08-24
A small annoyance:

Whenever I install an snap my main audio gets set to 45%. It's a very minor annoyance as it's easy to set my sound back to the correct level, but I am curious as to why this is happening. I can find no reference to the same issue via google or ubuntu forum search.

Xubuntu 23.04

---

### Post by Rubi1200 on 2023-08-27
Curious indeed since snaps usually have limited access to system resources.

Do you recall the last snap package you installed?

Is there anything unusual in the logs?

```
dmesg | grep -i audio

```

---

### Post by fefniir2 on 2023-08-31
Sorry this took so long to reply!

I just installed gnome system monitor snap. The audio did get set to 45% but then immediately got set back to it's original level. First time I've seen that happen.

dmesg | grep -i audio

produced no output before or after installing the snap.

---

### Post by Rubi1200 on 2023-08-31
Also never heard of such a thing. Perhaps it was just a one-off occurrence/bug/oddity?

If sound is back to normal I guess this is kind of solved?

---

### Post by fefniir2 on 2023-09-02
Looks like it does resolve itself. Should I mark this as "Solved"? Is there a "Sort-of Solved" tag?

---

### Post by Rubi1200 on 2023-09-02
I guess leave it open for now since we cannot really say it is solved. No, there is no "sort of solved" tag :-)

---

