---
title: "Splash screen chnage after KDE installation"
date: 2012-05-28
forum: Desktop Environments
---

### Post by nikhil14 on 2012-05-28
I installed Ubuntu 12.04. 
I also installed KDE4.8.
I changed my display manger to kDM and afterwards I changed it back to lightDM (Ubuntu default).
Command:
sudo dpkg-reconfigure lightdm

Now when I am booting the machine, it is still showing the splash screens of KDE, although afterwards it goes to Unity log-on screen as expected. Same thing happens at shut-down or log-off - it shows splash screens of KDE.

PS:
This is the first time I am starting any thread at any public technology forum, so please forgive me if my question is silly or already answered. Please guide me to the right thread if it is already answered.

---

### Post by zombifier25 on 2012-05-29
The boot screen has changed to that of Kubuntu's. To change back to that of Ubuntu's, type this command:
```
sudo update-alternatives --config default.plymouth
```
then choose the choice ubuntu.logo. For example, if the choice for ubuntu.logo is 0, then type 0 and Enter.

---

### Post by nikhil14 on 2012-05-29
Thanks a ton for your quick reply!
I used the command:

sudo update-alternatives --config default.plymouth
After using the command I made the changes as suggested by you.
After the changes I can see the selection like this:

 Selection                                        Path                                                                     Priority         Status
---------------------------------------------------------------------------------------------------------------------------------------------------
   0           /lib/plymouth/themes/kubuntu-logo/kubuntu-logo.plymouth   150           auto mode
   1           /lib/plymouth/themes/kubuntu-logo/kubuntu-logo.plymouth   150           manual mode
* 2           /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth        100           manual mode

But, still same problem persists!!!
Thanks!

---

### Post by thomsebastin on 2012-05-30
> **nikhil14 said:**
> Thanks a ton for your quick reply!
I used the command:

sudo update-alternatives --config default.plymouth
After using the command I made the changes as suggested by you.
After the changes I can see the selection like this:

 Selection                                        Path                                                                     Priority         Status
---------------------------------------------------------------------------------------------------------------------------------------------------
   0           /lib/plymouth/themes/kubuntu-logo/kubuntu-logo.plymouth   150           auto mode
   1           /lib/plymouth/themes/kubuntu-logo/kubuntu-logo.plymouth   150           manual mode
* 2           /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth        100           manual mode

But, still same problem persists!!!
Thanks!

I dono if this works,but it has always worked for me.
=>go to synaptic manager.
=>search for kubuntu plymouth,kde-plymouth or something similar until u find it ,or else you can even just search plymouth .
=>select the plymouth theme of kubuntu n remove it.(you can add it anytime later.)..
=>hope this work for u too.
regards 
-thomas

---

### Post by zombifier25 on 2012-05-30
> **nikhil14 said:**
> Thanks a ton for your quick reply!
I used the command:

sudo update-alternatives --config default.plymouth
After using the command I made the changes as suggested by you.
After the changes I can see the selection like this:

 Selection                                        Path                                                                     Priority         Status
---------------------------------------------------------------------------------------------------------------------------------------------------
   0           /lib/plymouth/themes/kubuntu-logo/kubuntu-logo.plymouth   150           auto mode
   1           /lib/plymouth/themes/kubuntu-logo/kubuntu-logo.plymouth   150           manual mode
* 2           /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth        100           manual mode

But, still same problem persists!!!
Thanks!

Forgot an extra command to apply your changes:
```
sudo update-initramfs -u
```

---

### Post by nikhil14 on 2012-05-30
> **zombifier25 said:**
> Forgot an extra command to apply your changes:
```
sudo update-initramfs -u
```

Thank you, [zombifier25]("http://ubuntuforums.org/member.php?u=1251447")!
That worked out just fine....

I am sure I will enjoy this cup of Ubuntu!!!
Thanks!!!!

---

