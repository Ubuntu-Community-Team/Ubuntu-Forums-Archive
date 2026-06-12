---
title: "Can't start x, no screens found."
date: 2005-11-18
forum: Desktop Environments
---

### Post by Mezzoforte on 2005-11-18
I get the error: "Fatal server error, No screens found." when I try to start x. I have tried the 
```
dpkg-reconfigure xserver-xorg
``` and installing the latest nvidia drives with ```
apt-get install nvidia-glx
``` and ```
nvidia-glx-config enable
``` but with no success.
Does anyone have an idea about what to do next?

---

### Post by Kyral on 2005-11-18
I actually had this happen to me after my misadventure in playing with the filesystem (as with most misadventures in Linux I learned a lot about whatever I was messing with in the process) last night. 

It seemed the Nvidia module itself wasn't being loaded. First check to see if this is the case by running ```
lsmod
``` and looking for "nvidia". If it isn't there then

```
sudo depmod -a && sudo modprobe nvidia
``` 

to load the module. Then try starting X

---

### Post by Mezzoforte on 2005-11-18
Thanks, but when I did that I got this error:
FATAL: Error inserting nvidia (/lib/modules/2.6.12-9-386/volatile/nvidia.ko):
No such device

---

### Post by Mezzoforte on 2005-11-27
Well, then if I can't solve that, is there any way of restoring the old kernel again? I tried just to choose it in the GRUB menu, but the graphical interface didn't work there either after installing the new kernel. Anyone have a suggestion?

---

### Post by Fittersman on 2005-11-27
your problem sounds very simmilar to the one i had. Search for "x server problem", there are two threads i created and they should help you out.

---

### Post by Mezzoforte on 2005-11-28
Thanks! It solved that problem. Now I have some other problems, hehe...

---

