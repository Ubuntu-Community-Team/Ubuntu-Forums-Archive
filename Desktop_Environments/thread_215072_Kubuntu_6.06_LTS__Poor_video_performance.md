---
title: "Kubuntu 6.06 LTS / Poor video performance?"
date: 2006-07-13
forum: Desktop Environments
---

### Post by john14x2 on 2006-07-13
I have a Gateway g6-350, which has a Pentium II 350mhz processor, 256mb ram, and a 20gb hard drive. Kubuntu appears to run fine, however when it  comes to something like playing a wmv video, or something like on youtube.com, The video is very choppy, even when the flash plugin is adjusted to the lowest quality settings. I've also tried some kind of settings in kaffine for the lowest quality also / cpu usage. I previously used Windows 2000 on this system, and they werent a problem, even with the built in driver. The video is onboard, I believe its a Nvidia Riva 128ZX, 8mb. I thought that perhaps the nvidia drivers would perhaps help this, however I am not sure as if they support my device. I would REALLY prefer not to use windows, so any suggestions?

---

### Post by DarthMandeep on 2006-07-13
You should try installing the legacy version of the Nvidia driver. Newer versions of the driver don't support older cards.

I'd also suggest basic tweaks, like ensuring that your hard disks have DMA enabled by using the hdparm program, editing your /etc/X11/xorg.conf file to make use of options like accel and FastVram, setting your video player to use Xv if it's supported, etc,.

---

### Post by linuxnewbie946 on 2006-07-13
> **john14x2 said:**
> I have a Gateway g6-350, which has a Pentium II 350mhz processor, 256mb ram, and a 20gb hard drive. Kubuntu appears to run fine, however when it  comes to something like playing a wmv video, or something like on youtube.com, The video is very choppy, even when the flash plugin is adjusted to the lowest quality settings. I've also tried some kind of settings in kaffine for the lowest quality also / cpu usage. I previously used Windows 2000 on this system, and they werent a problem, even with the built in driver. The video is onboard, I believe its a Nvidia Riva 128ZX, 8mb. I thought that perhaps the nvidia drivers would perhaps help this, however I am not sure as if they support my device. I would REALLY prefer not to use windows, so any suggestions?

Does it stream faster in Windows? If not, then its probably your processor thats slow.

---

