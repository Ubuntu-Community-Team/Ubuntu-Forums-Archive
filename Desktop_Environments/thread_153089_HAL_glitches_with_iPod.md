---
title: "HAL glitches with iPod"
date: 2006-03-31
forum: Desktop Environments
---

### Post by janusloo on 2006-03-31
Hi there,

First of all, I am not a newbie on Linux. I have tried zillion linux distros before to use as my desktop but I always went back to Windoze desktops. Not that I don't like Linux. On the contrary, I have been running Linux on my home servers for years now and am very happy with it. The reason I went back to Windoze was becos Linux in that time (few years back) was not really ready for the desktop. But this time Linux is ready and I am gonna stick with desktop Linux on Ubuntu! :-)

And after browsing the forum for days hoping to find answers to my problem to no avail, I decided to create this thread to see if someone out here can help me with my mysterious HAL problem. It's actually not a big problem but a cosmetic one. I will explain it in details:

HAL, hotplug, udev and other hotplug related functionalities work on my box without any problem. I can load a CD/DVD and it gets mounted and shown on the desktop. Flash drive, USB keys and USB storage drives work as expected too. The problem surfaces when I tried to connect my iPod. When my iPod is plugged in, iPod displays neatly the message: Do not disconnect. lshal also shows that it found the iPod and dmesg showed that it is plugged in. And when HAL (or hotplug I don't know which one) tried to scan the filesystem to determine what FS is on the iPod partition, it only scanned the first one and complained that no supported FS is found and the iPod partition is not mounted. This behaviour is correct since the 1st partition on the ipod is the firmware partition. Linux can't read it anyway. But why HAL does not go on scanning iPod and detect the 2nd partition where all the songs reside? I could however pmount /dev/sde2 and it gets mounted and symlinked to /media/sde2. I could also mount /dev/sde2 to /media/ipod.

My question is: how can I let Ubuntu automount the 2nd partition on the ipod? Or is this a bug/limitation in hotplug/hal that it can't handle removable drives with more than one partition? And strange thing is: I have a USB external drive. If I first connect the USB drive, the USB drive would get connected and mounted and created an icon on the desktop. But if I first plug iPod in, manually mount it and then plug in the USB drive, it does not get mounted automagically. So if I wanted to get the USB drive automounted, I have to do it in the following sequences:

- plug in USB drive
- plug in iPod
- mount iPod 2nd partition manually

All other hotpluggable devices work flawlessly and all get automounted when they get connected. Only iPod and USB drive won't get automounted. Does anybody know why is this?

My system has the latest kernel version 2.6.12-10-386 and all pending updates have been applied. I have a video ipod. My ipod is FAT32 formatted. I could work with my ipod without any problems in Ubuntu with gtkpod incl. video syncing, smart playlists and things like that. I can also encode mp4 video with aac support. I only want to know why my ipod does not get automounted. I read that many people have this problem and I also tried adding users to the hal group and things like that but still it did not solve the problem.

I am tempted to reinstall everything to check if a fresh copy of ubuntu works but since I spent countless sleepless nights to make my Linux box usable and productive like it is right now, I am really reluctant to do that, unless nothing helps.

I can work on my box no problem only I want my ipod to be automounted. Can someone please help me out or give me info why this behaviour in Ubuntu breezy? Thanks!

---

### Post by janusloo on 2006-03-31
Strange thing is: hotplug works well with all other removable drives but not ipod. HAL seems to try to mount the 1st partition but the real data resides on the 2nd partition. Is there a way to tell HAL to mount the 1st one instead of 2nd partition? This is very annoying as hotplug works flawlessly with other hot-pluggable drives. Can anyone help me with this? Please?

---

### Post by janusloo on 2006-04-01
Phew, after troubleshooting for the past 2 days I finally found out that the problem I have has nothing to do with the hal, gvm, hotplug or whatsoever. I connected my ipod to my friend's pc and restored the ipod to its factory default. Now I can just plug it in and viola, the cute little ipod icon appeared on my desktop!! So my advice to you guys here who have problems getting their ipods automounted, you should restore your ipod to its factory default. You should only do this if you know that your hal, hotplug and udev are working correctly. In my case it is becos all other removable devices get recognized without any problems and automounted, only my ipod not.

Am really really happy now!!! :-)

---

