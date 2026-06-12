---
title: "new vid card...will this xorg.conf be a problem?"
date: 2007-03-14
forum: Desktop Environments
---

### Post by Lymen on 2007-03-14
I know... beryl is in development and it can break my system,  but its SO pretty .
I want it.

So I bought a new nvidia e-Geforce6200 le to replace my ATI radeon 7500.

before I installed the new card, I installed the nvidia driver.  installed the new card, rebooted and everything seems to work...but just out of curiosity I checked my xorg.conf and saw this:

Section "Device"
    Identifier     "ATI Technologies, Inc. Radeon RV200 QW [Radeon 7500]"
    Driver         "nvidia"
EndSection


Identifier still says ATI!
does this matter?  should I change it? did I break anything?  is this a dumb question?:redface:

---

### Post by louis_nichols on 2007-03-14
Hi! Don't worry about the question, it's not dumb. Xorg is one of the most complicated things in Linux, imo.

The answer is that you should reconfigure your xorg.conf. This can be done automatically by running the command:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Next thing you have to do is to install the nvidia proprietary driver. The wiki on the beryl site has instructions on how to do this. Make sure you run the command ```
sudo nvidia-xconfig
``` at the end of the process.

After this, you will be all set. Only thing remaining will be ot install beryl and enjoy!

---

