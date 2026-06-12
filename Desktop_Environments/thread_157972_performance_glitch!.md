---
title: "performance glitch?!"
date: 2006-04-10
forum: Desktop Environments
---

### Post by morpheus_clio on 2006-04-10
Hi all ... 

today I was wondering around in the internet (using firefox) and listening some music when I downloaded a 30 megs file ... (linux kernel ok!) ...well my problem started when I unpacked the file ... the sound started to kinda stop and even the "mouse" had problems moving around the desktop! ... after the unpack the performance went normal and the system was responsive again... so my question ...

Is this normal? It was a little 30 mg file and I was just listening an mp3 and reading a webpage...

the files are in another disk NTFS partition ...
the site was a web forum (no flash weird things) and the music player was Rhythmbox 0.9.1

NOTE: I've suposedly use the automatix patch to turn on DMA ... but I can confirm if its working or not! ... the automatix crashed and didn't install some things but the automatix warns to NOT repeat the process again (turning the DMA on)

---

### Post by AndrewJ on 2006-04-11
Installing packages (especially ones which contain many smaller files) can be quite intensive on disk I/O. This can affect your system performance as resources are directed to disk operations, also if you're playing an mp3 from the same drive that you're reading/writing elsewhere can cause skipping in playback.

In short, yeah it's quite normal :P

---

