---
title: "Performance Issues Hearts of Iron 4"
date: 2018-01-08
forum: Gaming &amp; Leisure
---

### Post by leo1798 on 2018-01-08
I recently made the switch to Ubuntu 16.04 from Windows 10 as I could no longer bear how buggy and intrusive it was, and today I attempted to play my first game: Hearts of Iron 4. 

On Windows 10, I rarely experienced lag issues, at least until the late game, running medium-high settings, but I was disappointed to experience significant lag as soon as I opened up the game running the same settings. I had to drop my settings down significantly to get the game to be playable. I also ran Civilization V and Portal 2 on their respective maximum graphical settings, however I experienced no issues, if not better performance than with Windows. To my knowledge these games are more intensive on the GPU while Hoi4 is more intensive on the CPU; correct me if I'm wrong. I enabled the proprietary driver for my graphics card, and also enabled the open source driver setting for my CPU in the additional drivers tab.

I use a multi-purpose laptop with the following specs:

512 GB SSD
16 GB RAM
1 GB NVIDIA GTX 950M Graphics Card
Intel i7-6500U 2.5 GHz Processor
4K Display (3840x2160)

If anyone could help or give me advice, that would be fantastic and greatly appreciated.

---

### Post by mastablasta on 2018-01-09
HOI if you turn off various GPU stuff (not sure why it is needed in such a game) is indeed more CPU intensive game than anything else. 

Are you playing  a native version or via Wine? 

software performance depends on many things. it could be that linux version is not done well. though i haven't noticed anything on the web. it could be the drivers need an update. by adding nvidia PPA you should be able to pull newer drivers to the OS. but it really is hard to say what is the issue here. it could just be that a certain game setting is off.

did you try to monitor PC while running the game? for example with top or htop in terminal? just to see what is actually causing the lag and slow down. to figure out if it is CPU or GPU related.

with games it is usually quite tricky to figure it all out. not long ago i played far cry 2 on my old PC. the PC should be able to run high settings easily. yet it lagged. but it also lagged when i reduced all settings to minimum. not more not less. just lag. overall it looks like my GPU is to blame. but changing many settings i could not improve it. either low , medium or high lag was always there one moment and gone the next.

---

