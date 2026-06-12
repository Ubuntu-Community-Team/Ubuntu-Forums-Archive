---
title: "Nvidia Drivers kicking my ***, help appreciated!"
date: 2009-05-23
forum: General Help
---

### Post by mechtech256 on 2009-05-23
Hey guys, I recently built a couple computers for running Ubuntu with multiple screens. The hardware is a standard mobo/C2D/160g SATA hd, and each computer has 2x Nvidia FX5200 PCI GPUs.

I can install Ubuntu 9.04 and get the GUI up just fine. After this point, I've tried 2 separate solutions.

On the first computer I ran the Nvidia .run file and installed the 173 driver that way. After the restart, I'm stuck in a command line environment, and typing "startx" gives me "no devices detected" and "no screens found".

On the 2nd computer I had a fresh install and went straight to the terminal and installed the text version of Envy. I ran envy and selected the recommended 173 drivers (which people say works with the FX5200). Envy went through the install just fine, but once again, after the restart I'm stuck in the command line interface.

I also tried to install 8.04, because I figured there was a chance Envy would configure everything correcty there, but when I run the 8.04 install CD the partition selection screen is blank, even though the hard drive has 80 gigs of free space and another 80 gigs dedicated to the 9.04 install. Gpartition (or whatever it's called) shows no partitions as well, so I gave up on 8.04.

Anyway, if someone can give me a quick fix, or give me step by step instructions on how to get the nvidia drivers up from a clean 9.04 install I'd greatly appreciate it. Go as fine detail as you like, such as should I just have 1x fx5200 plugged in to start, or if I have both cards in should I have 2 monitors plugged in as well during the installation, ect. I've put about 10 hours into this so far and I really need to get these computers up and running!

---

### Post by Kareeser on 2009-05-23
I'm betting it's your use of SLI... I don't have any experience with that, but this may help in your quest :)

[http://us.download.nvidia.com/XFree86/Linux-x86/180.51/README/chapter-25.html](http://us.download.nvidia.com/XFree86/Linux-x86/180.51/README/chapter-25.html)

---

### Post by smurfgod on 2009-05-23
I have the Geforce mx440 and can run duals screens but can't get them to be independent.Hope you figure it out man cuz I'm sorta in the same boat as you.

---

