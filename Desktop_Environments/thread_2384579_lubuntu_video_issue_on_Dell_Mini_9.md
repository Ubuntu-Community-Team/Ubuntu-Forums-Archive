---
title: "lubuntu video issue on Dell Mini 9"
date: 2018-02-08
forum: Desktop Environments
---

### Post by ricardus2 on 2018-02-08
So I finally found a cheap battery for my 7 year old Dell Mini 9, and figured I'd resurrect it. It came with Ubuntu right from Dell (I think it was 10.04 LPIA LTS) and I eventually installed regular Ubuntu 12.04 when I found out they had a video driver and I didn't have to use the proprietary one from Dell. I upgraded to 14.04, and then the battery died and I had a new laptop, so I chucked the Mini 9 in a drawer for future experimentation.

 Anyway, With the new battery I decided to install lubuntu 17.10.1 

 Everything went great with the install. The video displayed fine for the whole install, then it finished and needed a reboot, and when it rebooted the video was screwy. Only the rightmost 1/5th of the screen had a desktop on it. You could see the Shutdown button and what not (but the shutdown feature didn't seem to work). The other leftmost 4/5ths of the screen was just black, with some squigglys on top of the screen. You could move the mouse over the entire screen though.

 Does this have something to do with that video driver? Has anyone ever seen this before? Any ideas for a quick fix?

---

### Post by ricardus2 on 2018-02-08
A friend on the internet tried an install on his Mini 9 and the same thing happened.

---

### Post by ricardus2 on 2018-02-09
OK, so I didn't find this thread the first time I looked, but a friend found it:

[https://ubuntuforums.org/showthread.php?t=2376765](https://ubuntuforums.org/showthread.php?t=2376765)

So you first need to edit Grub at boot like they say:

[COLOR=#000000]change 3rd line of grub on bootup to [/COLOR]
[COLOR=#000000]grub_gfxmode=1024x600

 Hit CTRL-X to boot. Then open a terminal and edit the grub file per this:

[/COLOR]https://askubuntu.com/questions/19486/how-do-i-add-a-kernel-boot-parameter

But you need to add this line:

GRUB_GFXPAYLOAD_LINUX=1024x600

We added it under the commented out "GRUB_GFXMODE" line.

 Then save, and update grub like normal. Reboot and video should be fine.

For whatever reason lubuntu was booting up into an unsupported video mode, despite working fine during install, and working fine when running a live distro.

Anyway, I hope this helps.

---

### Post by mörgæs on 2018-02-09
Good, if you consider the problem solved please mark the thread so.

It affects various Atom computers. Here is some background information: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1724639](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1724639)

---

### Post by ricardus2 on 2018-02-10
I have no idea how to mark it solved.

---

### Post by wildmanne39 on 2018-02-10
Click on the solved threads link in my signature for directions.

---

### Post by wildmanne39 on 2018-02-10
Please use thumbnails or url's when posting images because many people have slow or limited connections.

---

