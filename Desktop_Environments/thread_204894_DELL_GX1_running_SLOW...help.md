---
title: "DELL GX1 running SLOW...help"
date: 2006-06-27
forum: Desktop Environments
---

### Post by reckless2k2 on 2006-06-27
I've got a DELL GX1 PIII 450MHz with 384MB of RAM. I'm dual booting Ubuntu 6.06 and Windows XP. Ubuntu is painfully slow. I'm using the 686 kernel versus the 386 kernel with no difference. XP is running quite fast to my surprise. Is there a tweak I need to run? Video and music playback is choppy or won't run even though DMA is turned on.
Any ideas if there is something I can do rather than switching to a different desktop enviroment? I'd rather not move from GNOME. 
Thanks.

---

### Post by rai4shu2 on 2006-06-27
Could you specify your hard drive and video card details?

---

### Post by reckless2k2 on 2006-06-27
EIDE 7200RPM 250GB HD and integrated Intel graphics card (4MB) shared with onboard RAM.

---

### Post by reckless2k2 on 2006-07-30
I know there were views on this thread so I figured others had similar circumstances. I figured I'd throw out what I did to ultimately optimize my preformance. I followed some suggestions on the thread about maximizing Ubuntu preformance. I did the following:

1 - recompiled my kernel for P3 with low memory
2 - installed and ran prelink 
3 - disabled unnecessary boot processes
4 - installed swiftfox

These simple tweaks enabled me to keep GNOME and speed up preformance.

---

