---
title: "cant get sound on mini 9"
date: 2009-01-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by fiowantscoffee on 2009-01-02
hi,

i've installed ubuntu 8.10 on my mini dell with wubi, and i can't get the sound to work. i followed the tutorial [here]("http://ubuntuforums.org/showthread.php?t=1026259") but when i rebooted the sound still didn't work. i've tried redoing it to see if i did anything wrong but the file comes up blank.

any help would be greatly appreciated!!

---

### Post by anjilslaire on 2009-01-02
[http://ubuntuforums.org/showthread.php?t=917187]("http://ubuntuforums.org/showthread.php?t=917187")

> 
4) Sound

```

sudo nano /etc/modprobe.d/alsa-base

```
add the line to the end
```

options snd-hda-intel model=dell

```
reboot the pc

on reboot double click on the sound icon in the toolbar

increase the speaker volume


---

### Post by fiowantscoffee on 2009-01-02
great!!! thank you :D

---

### Post by anjilslaire on 2009-01-02
no problem. In future, the forums have a way to record "thanks". Click the little yellow medal on th bottom-right of a users post to "thank" them. It helps track useful posts for everybody. 
Just a little FYI to help you get started, and Welcome to the Forums! :)

---

### Post by vbt on 2009-02-03
I don't see a little medal so here, thank you thank you thank you.  I've been looking for a solution to the no sound problem for 2 days now.  This worked.  :p

---

### Post by newone on 2009-02-09
Thanks to this post! Finally, a solution to the "no sound" problem.

---

### Post by lmbevard on 2009-02-10
> **anjilslaire said:**
> [http://ubuntuforums.org/showthread.php?t=917187]("http://ubuntuforums.org/showthread.php?t=917187")

I've been trying to find this answer for a week. Tried many things but after trying a couple of times got this to work.:P

---

