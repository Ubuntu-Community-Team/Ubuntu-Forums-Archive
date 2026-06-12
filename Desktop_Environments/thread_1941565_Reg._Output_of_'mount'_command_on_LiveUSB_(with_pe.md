---
title: "Reg. Output of 'mount' command on LiveUSB (with persistence)"
date: 2012-03-15
forum: Desktop Environments
---

### Post by bpraveen on 2012-03-15
I am running Lubuntu 11.10 off a usb-stick (with persistence).

I thought that the output of 'mount' command I noticed on my Lubuntu was strange.

> 
ubuntu@ubuntu:~$ mount | grep 'cow'
/cow on / type overlayfs (rw,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=600,commit=600,commit=0,commit=600,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=600,commit=600,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0)


I have suspended and resumed the computer many times and I am guessing that the repeated 'commit=' values are probably a result of that.

Is this expected on a LiveUSB+persistence? Do I need to take any action?

Where can I find out additional information about this?

---

### Post by marinara on 2012-03-17
write up instructions to reproduce and file a bug

---

### Post by bpraveen on 2012-03-20
> **marinara said:**
> write up instructions to reproduce and file a bug

Sure. I will do that. Thanks.

---

