---
title: "Where are updates and downloaded software stored"
date: 2010-05-01
forum: Desktop Environments
---

### Post by Bursal on 2010-05-01
Hi Ubuntu 9.10 noob here! Can I access downloaded updates and software downloaded via the Software center? I am trying Ubuntu or a series of machines and have limited downloads. It would be great to be able to move from machine to machine with only one download.

Thanks in advance
Di

---

### Post by autocrosser on 2010-05-01
All downloaded .debs are in /var/cache/apt/archives. I just take a USB stick & copy the files from computer to computer--you will need root permissions to copy to the target--not from the source to the stick--I do gksudo nautilus on the target computer & then copy from the stick.

---

