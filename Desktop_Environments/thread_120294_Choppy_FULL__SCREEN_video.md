---
title: "Choppy FULL  SCREEN video"
date: 2006-01-21
forum: Desktop Environments
---

### Post by ashrack on 2006-01-21
Why must I install NVIDIA drivers to watch movies(mpeg,divx,dvd,wmv) in full screen else I get a choppy and interlaced video no matter which player am using.
On my desktop computer where I have a RADEON card I can watch movies in full screen with the native BREEZY drivers.
Is there a way to watch movies in full screen using the native BREEZY drivers?

ps. for those wondering why I wouldn't want to install NVIDIAs the answer is simple, they break my [HIBERNATION]("http://ubuntuforums.org/showthread.php?t=75443&highlight=suspend2"). Even thou I followed "[HOW TO get Hibernate working with Proprietory Nvidia driver (using Suspend2)]("http://ubuntuforums.org/showthread.php?t=79295")" guide
DMA is enabled

---

### Post by asq on 2006-01-21
Might be a newb answer but for dvd playback maybe a

```
$sudo hdparm -d1 /dev/hdc
```

---

### Post by ashrack on 2006-01-21
Tanx for your reply but this doesn't have anything to do with DMA. Because with NVIDIA drivers all works great only with the native BREEZY drivers I have corruptions when in FULL SCREEN mode

---

### Post by ashrack on 2006-01-21
bump

---

### Post by ashrack on 2006-01-22
bump

---

### Post by ashrack on 2006-01-23
must I really install NVIDIA drivers to watch full screen video? I really wonder how come it works fine on a RADEON card

---

### Post by ashrack on 2006-01-24
since apperantly theres no fix for this issue.
I would just like to ask if others using the NV driver also get interlace video when in full screen mode?

---

### Post by ashrack on 2006-01-24
since apperantly theres no fix for this issue.
I would just like to ask if others using the NV driver also get interlace video when in full screen mode?

---

### Post by void_false on 2006-01-24
Try switching video options in your player. At least that helped me.

---

### Post by ashrack on 2006-01-25
VOID
tried them all, and none works.

---

