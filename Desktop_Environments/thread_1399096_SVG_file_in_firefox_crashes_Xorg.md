---
title: "SVG file in firefox crashes Xorg"
date: 2010-02-05
forum: Desktop Environments
---

### Post by aiwarrior on 2010-02-05
Hi
Recently i have been coding to generate svg files but while testing i came upon a file that when opened in firefox freezes X. I don't think its a firefox issue as if i quickly switch to the tty0 and do execute top command it shows firefox isn't abnormal and doesn't crash but X shows 800mb worth of memory usage all of a sudden and iotop show 10Mb/s of disk read access only. 
The whole system becomes unresponsive and most of the times must be hard rebooted. I can reproduce the behavior in my machine and would like for you to test the file to know if the same happens your machines. This problem only happens when i open the svg file in firefox. Other browsers/image viewers don't seem affected. If firefox is used in Windows the image renders fine.

The svg file is in annex. I would like your feedback to know if it's just my configuration

I am running firefox 3-5 karmic koala with intel drivers on Xorg

NOTE: This file can crash your system

---

