---
title: "No sound with Kubuntu64 8.10"
date: 2008-12-23
forum: General Help
---

### Post by Arukas on 2008-12-23
When Kubuntu opens and closes I have sound, but when I am running Kubuntu it has no sound at all.  I know my sound works, because I have a duel boot system.

Anyone have an idea how to fix this?

---

### Post by Xiong Chiamiov on 2008-12-24
Try [this]("http://ubuntuforums.org/showthread.php?t=205449"), post back with any problems.

---

### Post by Arukas on 2008-12-24
I followed the guide, Kubuntu reconizes my sounds cards, and the mixer was set fine, but there's still no sound.

---

### Post by wd5gnr on 2008-12-24
Do you have more than one sound card? Phonon on my similar setup constantly forgets what sound card I want to use. So I've wound up mostly bypassing it or just using the sound card it wants me to use (lame!). 

What does aplay -l say? Can you do an aplay on a wav file? What about an aplay -D with the specific device?

---

