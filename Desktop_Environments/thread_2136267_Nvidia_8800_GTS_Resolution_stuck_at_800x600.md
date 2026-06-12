---
title: "Nvidia 8800 GTS: Resolution stuck at 800x600"
date: 2013-04-17
forum: Desktop Environments
---

### Post by sealusp on 2013-04-17
Hey everyone!

I'm a long time admirer of Ubuntu, and I've finally decided to give it a try. I'm having some problems though, and be forewarned, I'm a total Linux noob.

 I've done a lot of reading into my problem, and I can't seem to get anything to work. I am currently on Ubuntu 12.04 64 bit, and I am using an Nvidia 8800 GTS. My monitor is an Acer monitor and it has a native resolution of 1400x1050. The issue is that I can only run Ubuntu using 800x600. No matter what driver I use, I am presented with no options besides 800x600 in "Displays" under System Settings. It also says my monitor is "unknown".

 I've tried installing several new drivers, and that isn't helped. My current driver version is 310.14 as shown in Nvidia X Server Settings, but I have tried others, and they have not worked either.

 I've also tried doing:

sudo apt-get update       
sudo apt-get install nvidia-current

 That hasn't helped either. If anyone could help me out, it'd be much appreciated! Can provide more information if needed. Lately, I'd like to be able to play some games on here, so I'm guessing it would be best to stay with new drivers.

---

### Post by mr.suchy on 2013-04-17
Hi

Did you modify you resolution manually ? In config file  ?

---

### Post by sealusp on 2013-04-17
Thanks for the quick reply. No I have not. How would I go about doing that? I tried earlier today, but couldn't seem to get it right.

---

### Post by kansasnoob on 2013-04-17
I recently encountered an issue with an nVidia C61 [GeForce 7025 / nForce 630a] (rev a2) graphics chip and the nvidia-current driver (version 304.88):

[http://ubuntuforums.org/showthread.php?t=2134340&page=2&p=12601403#post12601403](http://ubuntuforums.org/showthread.php?t=2134340&page=2&p=12601403#post12601403)

Not sure if the same solution will help you or not.

---

### Post by sealusp on 2013-04-17
Thanks for pointing me to that. I just did a fresh install of 12.04 and it seems that it is running 304.88, which is working correctly. Not sure why it wasn't working before. I'm temped to try to upgrade the drivers to 310.14, but I'm afraid I'll run into the resolution problem again.

---

