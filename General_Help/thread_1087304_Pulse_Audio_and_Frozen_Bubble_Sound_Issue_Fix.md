---
title: "Pulse Audio and Frozen Bubble Sound Issue Fix"
date: 2009-03-04
forum: General Help
---

### Post by yeaitsdark on 2009-03-04
Hey I just wanted to share this if anyone else is having this issue. My problem was that Frozen Bubble was playing sound via my USB Blue Tooth and not out of my speakers. Also, it was seemingly glitching with pulse audio. I was unable to move the stream as it kept "flickering".

After some researching I found this thread: [http://ubuntuforums.org/showthread.php?t=27595](http://ubuntuforums.org/showthread.php?t=27595)

Which tells to install libsdl1.2debian-all. Which did not solve my problem, but when installing aptitude mentioned that "Package libsdl1.2debian-pulseaudio is not installed." So I figured, why not?

This is in Ubuntu 8.10 64bit. In short here is the solution:

```
sudo apt-get install libsdl1.2debian-pulseaudio
```

---

