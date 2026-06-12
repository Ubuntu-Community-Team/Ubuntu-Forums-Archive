---
title: "hady beta livecd resolution"
date: 2008-03-23
forum: Development CD/DVD Image Testing
---

### Post by jepong on 2008-03-23
I downloaded Ubuntu 8.04 Beta installer to be instaled on my IBM ThinkPad R30 (2656-40J). This is a Celeron 800mhz and 768MB RAM.

When the LiveCD is finish, I was given an 800x600 resolution. Thinking this was a normal resolution for installation so I continued. After booting my machine with freshly installed Hardy Heron beta, my resolution was 800x600. I tried to increase it to 1024x768 but 800x600 was may maximum resolution.

How could that be? I installed Gutsy and my initial resolution was 1024x768. I tried to update gutsy to hardy beta and everything is ok. But i still want a freshly installed ubuntu.

P.S. i also downloaded HArdy Alpha 6 before and LiveCD is also 800x600. I think its a video driver problem by ubuntu.

---

### Post by talsemgeest on 2008-03-23
Same thing for me. I'm guessing it is simply because it is only the beta, and they haven't implemented the higher resolutions yet.

---

### Post by 67GTA on 2008-03-28
If your proper res is not detected, you need to post a bug report on xorg for your hardware. I had the same problem because of a bug in the "nv"driver which has been fixed. The xorg devs need your help in getting the new xorg as bug free as possible. Check out this thread: [http://ubuntuforums.org/showthread.php?t=735118](http://ubuntuforums.org/showthread.php?t=735118)

---

### Post by Zyphrexi on 2008-04-04
running the beta livecd I had the same issue, though it didn't bother me all that much, it was just somewhat annoying.

I figured it had to do with the monitor not being recognized and also the usage of the 'nv' driver instead of nvidia

---

