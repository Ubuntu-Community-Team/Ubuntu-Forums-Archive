---
title: "Ubuntu 20.04.3 LTS hang during bootup, please help"
date: 2022-02-13
forum: Desktop Environments
---

### Post by harrysheng00 on 2022-02-13
Fresh install of Ubuntu 20.04.3 LTS on SATA SSD on Lenovo w530; ubuntu boot only, [COLOR=#ff0000]**not**[/COLOR] dual boot of ubuntu and windows.

Install was successfully, but never be able to bootup ubuntu deskup normally from right after the installation finished.
I always have to turn the power off and on a couple times to bootup into the desktop after I shutdown the machine or put it into suspended mode.
The bootup hangs at different places each time, have tried all different methods I could find on internet trying to clear the problem, none worked for me.

I can always bootup the desktop environment after a couple power off and on, without explicitly going through the recovery mode in the grub menu.
After it's booted into the desktop environment, the system seems work fine. I haven't experienced any other problems yet.
Have tried jdk-17, python, docker, eclipse on the system, so far as good. Works well with KVM to share keyboard and monitor as well.

Really do not understand why have to go through this painful process to boot it up after shut it down or put it into suspended state.

Could someone help me, please!

---

### Post by Autodave on 2022-02-14
Can you boot the machine OK with your installation medium?  I am thinking that either you got a bad download or a bad install.  If it were my machine, I would do a new dl and install and see if anything changes.

---

### Post by Skaperen on 2022-02-16
do you have more than one storage device, even if one is a USB memory stick?  if yes, it may be randomly giving different devices different hardware addresses like mine does.  be sure you are booting with exactly one storage device.  unplug any spare USB devices.  if you already have only one, then never mind.

---

### Post by him610 on 2022-02-17
This may give you some idea where it is hanging....
```

systemd-analyze && systemd-analyze blame

```

---

