---
title: "Need to reload X configuration"
date: 2011-02-22
forum: Desktop Environments
---

### Post by netwired on 2011-02-22
I have run into a problem with a existing workstation I can't seem to figure out. My configuration:

Ubuntu 10.10 64
ASUS M2N68-AM Plus MB w/ Nvidia Geforce 7025 graphics.

Has been running for almost exactly one year beautifully. System suddenly froze. When I rebooted, system stopped with message saying it could not detect graphics or KB or mouse. I suspected hardware failure but when I booted from live CD, It ran fine. I then ran e2fsck -c and found no bad blocks but 1 messed up inode which it fixed. 

I assume at this point the only problem is some lost configuration on video. I first tried apt-get nvidia drivers. this got rid of the message but now X will not start because of "no valid modes". Tried running  nvidia-xconfig but it exits without changing anything.

All user files seem to be OK. I'm not going to have to nuke this thing just to restore X am I?

Any ideas would be appreciated.

---

### Post by Frogs Hair on 2011-02-22
Hi and Welcome

This is a terminal command to restart X  and return to login.```
sudo /etc/init.d/gdm restart
```

---

