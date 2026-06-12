---
title: "Z210 Workstation"
date: 2012-08-22
forum: Desktop Environments
---

### Post by splintter on 2012-08-22
Hi,

I have installed a fresh new machine HP Z210 Workstation with a nvidia quadro 600, but i had some problems...

First, i installed Ubuntu 12.04 LTS but the grub didn't get installed correctly, and broken my Windows 7/Ubuntu dual booting. I did corrected it with a Live CD.

After that, when booted it my graphic drivers wasn't setup propertly and my resolution is 1024x768 (4:3)... and my monitor is a HP L200b with max of 1600x900 (16:9). I searched around the web and did some commands into my machine:

cvt 1600 900 75
xrandr --newmode "OUTPUT"
xrandr --addmode DVI-I-1 "1600x900_75.00"

and did successful changed my resolution to this. Now i need know how to stop my screen blinking...

If i installed nvidia drivers, the resolution get worst. (8xx per 6xx), Anyone knows?

---

