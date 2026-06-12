---
title: "where is hardware list?"
date: 2006-03-12
forum: Desktop Environments
---

### Post by Callatya on 2006-03-12
I need to know what it is that I'm running in the way of motherboard and processor. It sounds like an easy thing, i know :( I can't recall and I can't see it on the hardware itself. I know where I'd find it in XP :(

I have looked at the device manager (it looked likely) but it wasn't helpful. It appears to be *the* place to go, but I'm getting a bunch of "unknown" responses. Is this the correct spot? I have googled and it apears to be, but 'unknown' is rather unhelpful.

Is there some other way to get to this information or beat the device manager into submission? (if it involves the terminal, I'll need a step by step)

(eek, this was suppised to be in the newb section :( sorry guys!)

---

### Post by bjweeks on 2006-03-12
[QUOTE=Callatya]I need to know what it is that I'm running in the way of motherboard and processor. I can't recall and I can't see it on the hardware itself.

I have looked at the device manager (it looked likely) but it wasn't helpful.

Is there somewhere I can go to see?

(if it involves the terminal, I'll need a step by step)[/QUOTE]

System, Administration, Device Manger.

---

### Post by Callatya on 2006-03-12
oops, just edited first post while you were posting :(

Yes, I tried that, but it isn't giving me usable answers either in 'device' or 'advanced'.

---

### Post by kaamos on 2006-03-12
Here are some commands. Applications->Accessories->Terminal

lspci
cat /proc/cpuinfo
cat /proc/meminfo
sudo lshw

---

### Post by bjweeks on 2006-03-12
[QUOTE=Callatya]oops, just edited first post while you were posting :(

Yes, I tried that, but it isn't giving me usable answers either in 'device' or 'advanced'.[/QUOTE]

> less /proc/cpinfo

for cpu

---

### Post by Callatya on 2006-03-12
THANKYOU :) I feel all techie and clever now :)

---

