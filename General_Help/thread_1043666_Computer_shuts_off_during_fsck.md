---
title: "Computer shuts off during fsck"
date: 2009-01-18
forum: General Help
---

### Post by xnevermore on 2009-01-18
I recently decided to add Windows XP to my machine because I needed to use a specific Windows app (no, its not Wine compatible). I resized my main ext3 partition and added a FAT32 partition, then installed XP on it, but after using Windows for a while, the computer would shut off unexpectedly. If I restarted it right away, it would just shut off again before it finished booting (into either Windows or Ubuntu). I would have to wait awhile before turning my computer back on. Booting into Ubuntu works fine -- I can leave it on for days without any problems. I figured it might have been a partitioning or hard drive problem, so I used SystemRescueCD (a linux rescue live cd) to run fsck on my partitions, but when I do, the computer shuts off again, without fail.

Does anyone know what might be causing this problem? I'm running a Toshiba Satellite laptop with a Toshiba hard drive. How do I diagnose this problem? What's a good hard drive diagnostic utility I can use?

---

### Post by sirjoebob on 2009-01-18
Hey, Sorry to hear you are having issues. I would recommend downloading an iso of Hiren's boot disk. It has some hard drive checking utilities. It sounds like the issue may be HDD or other hardware. One way you can test it would be to run off of an Ubuntu live CD for a while to see if it has the same issues. If not, I would say its the disk, if so... perhaps it is the power supply.

---

### Post by xnevermore on 2009-01-18
Well, like I said, this problem only seems to occur when I'm running fsck off of a livecd or under windows. It doesn't happen under normal operation in Ubuntu. I've tried running the Ubuntu live cd normally without any problems. Often when a computer shuts down unexpectedly like this, its due to overheating, but its just strange that it'd only overheat in Windows and fsck. Anyway, I'll give the boot cd you mentioned a shot.

Other tips would be appreciated as well.

---

