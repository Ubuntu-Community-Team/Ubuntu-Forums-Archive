---
title: "Nvidia GeForce 8400M GS: Low performance in older Steam games"
date: 2013-12-03
forum: Gaming &amp; Leisure
---

### Post by schafml1 on 2013-12-03
I have consistently terrible frame rates under Linux in older games. Killing Floor, for example, is unplayable on anything other than 800x600 resolution and minimal video settings. CS:S is a slideshow. Portal starts out okay with minimal settings but slows down noticeably within a few minutes. On Windows everything runs fine, but I do everything else under Linux and I'm not willing to switch just for gaming. Here are the relevant specs (I'll post anything else if needed). 


Dell XPS M1330 (~5 years old)
4 GB RAM
120 GB Samsung SSD
Intel Core 2 Duo T8300, 2.40 GHz x2
Nvidia GeForce 8400M GS (using version 313 drivers)

Linux Mint 15 Olivia with Cinnamon DE (But I've also tried Xubuntu and had the same problems)


Am I correct in assuming that this should more than adequate to run games from the early to mid 2000's? Any ideas where the bottleneck might be? I'm not new to Linux and I'm willing to get my hands dirty to figure this out. Thanks for your help.

By the way, I've also posted the same question on the steam forums: [http://steamcommunity.com/app/221410/discussions/2/666827316273886739/](http://steamcommunity.com/app/221410/discussions/2/666827316273886739/)

---

### Post by dannyboy79 on 2013-12-03
i could play portal with a E4300 C2D and an Nvidia 8400GS just fine so I am guessing something is wrong with your driver installation. have  you tried an older or newer driver version?

---

### Post by schafml1 on 2013-12-03
Yeah, I've tried 304 and 310 with no improvement but I agree it sounds like a driver issue. I've tried installing 330 and 325 from the website but I haven't been able to do it without breaking X11. Is it possible the 313 driver is installed but not being used? Any good way to check?

---

### Post by schafml1 on 2013-12-03
Also, I get about 60 fps from glxspheres if that clears anything up

Update: FPS in glxspheres jumped to 150 after disabling sync to vblank in nvidia-settings.  I'll try running some games when I'm not sitting in class :)

Update: That wasn't the issue, fps is Portal is arguably worse than before

---

### Post by Arthur_D on 2013-12-03
Yeah you will most likely want sync to vblank as that minimizes tearing when playing games you would get over 60 FPS with, assuming your screen has a 60 Hz refresh rate (which is the most common).

---

