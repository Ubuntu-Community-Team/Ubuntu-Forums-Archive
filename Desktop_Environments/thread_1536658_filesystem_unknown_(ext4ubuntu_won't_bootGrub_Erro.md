---
title: "filesystem unknown (ext4/ubuntu won't boot/Grub Error 17)"
date: 2010-07-22
forum: Desktop Environments
---

### Post by schurtek on 2010-07-22
Suddenly, out of the blue, my PC stopped booting. It gave an error on Grub, Error 17 to be precise. So I googled to find what the problem was, and only after trying to get onto the drive through a live disk did I learn that I couldn't access the main harddrive where the linux partition was held. I kept getting a Unknown Filesystem error. 

 So I googled some more. But how do you google that? Eventually, I decided to run fsck on /dev/sda5 (the partition in query), and after half an hour of pressing Y over and over again, I was able to mount the partition from the live disk. Everything seems in order, so to speak. 

I have posted this here as I couldn't find anything on the forums and others sure could use this info.

What I do want to know, is how the hell this happened?

System was working fine, then it stopped working. Couldn't boot, even ran SeaTools to make sure the drive wasn't cooked.

Any insight would be good.

---

