---
title: "XScreenSaver freezes"
date: 2005-10-25
forum: Desktop Environments
---

### Post by blueturtl on 2005-10-25
After a failed attempt at switching to Breezy I decided it was time to go back to Hoary. Now I have reinstalled everything, but for some reason unknown to me I cannot set my screensaver.

The problem: everytime I try to, the window freezes almost instantly after which there is an enormous delay before it responds to anything (just the XScreenSaver window, overall system stability and responsiveness is still perfect). I finally ended up killing the process after the fifth time I tried it but I'm a bit puzzled as to what could cause this... My first Hoary install had no such problem.

Anyone run into this before? Help would be appreciated.

---

### Post by TristanMike on 2005-10-25
Have you upgraded your video drivers since this new install? I know that before I upgraded mine, I had loads of delay and time responsiveness problems, but they have gone away since updating. Just a thought.

---

### Post by blueturtl on 2005-10-25
Turns out the problem was caused by an external USB hard-disk. I was already beginning to suspect the sunspots, but after removing the drive (which consequently wasn't there before) all is now well. I used the external disk to backup my files, and it uses the USB 2.0 ports on my system. Apparently USB 2.0 on my system is some kind of a troublemaker. Luckily I only rarely use it.

What does transferring files over USB have to do with the XScreenSaver daemon? I don't know and I don't want to know. This is Linux for ya all :D

---

