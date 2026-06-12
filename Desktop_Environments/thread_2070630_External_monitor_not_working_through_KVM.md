---
title: "External monitor not working through KVM"
date: 2012-10-13
forum: Desktop Environments
---

### Post by vnfedotov on 2012-10-13
As i understand there is a lot of issues with KVMs and Ubuntu, but i haven't found this particular one.

So, here's my setup:
1. Fujitsu P701 Laptop with Ubuntu 12.04 
2. Trendent TK-409 KVM Switch both at home and at work
3. Old BenQ FP91G at home and Nec 1970NX at work
4. Several debian desktops both at home and at work

This is what happens:
1. initially, kvm connects monitor to one of the desktops;
2. when i plug in laptop, ubuntu shows that external display is connected (both in "Display" settings and xrandr ouput);
3. switch port so that now kvm connects monitor to the laptop;
4. for 3-5 seconds external monitor shows my ubuntu desktop, then switches off (xrandr output shows "VGA1 disconnected");
5. switch kvm back to desktop;
6. again, xrandr shows "VGA1 connected".

I expect it to work exactly opposite.

Few facts:
1. Issue repeats both at home and at work.
2. It works ok without KVM.
3. It worked ok with freshly installed ubuntu. Problems started after updates.
4. It worked ok with xubuntu.
5. After messing with xrandr i've managed to get it working properly, but after few hours external monitor switched off again and i've been unable to fix it back ever since.

Help, please. I start to think it would be easier to just set up debian properly.

---

### Post by vnfedotov on 2012-11-01
Still no fix, but i've figured out a workaround:
Problem resides somewhere between hardware, video driver and a switch. After connecting laptop to external display it works for a few seconds. If you've installed disper, you can even see it in available outputs, then hardware poller disables it. 

Obvious workaround is to disable the poller, it can be done this way:
echo N > /sys/module/drm_kms_helper/parameters/poll

It isn't great, starting xrandr or display settings will disable external display again, but at least it's working.

---

