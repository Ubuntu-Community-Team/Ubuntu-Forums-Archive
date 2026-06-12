---
title: "Dell D600 resume problem after suspend"
date: 2012-08-10
forum: Desktop Environments
---

### Post by wquatan on 2012-08-10
I have installed Xubuntu 12.04 on a Dell D600.

After a suspend (any method - via menu or lid close or power saving settings) the resume doesn't work

When I push the power button, the leds lid up, and that's all, no HDD activity.

I have to force a power-off and start the machine again.

What might be the reason ? What can I do ?

Further, when I do a hibernate, I get an error that I'm not authorized.

---

### Post by Toz on 2012-08-11
> **wquatan said:**
> I have installed Xubuntu 12.04 on a Dell D600.

After a suspend (any method - via menu or lid close or power saving settings) the resume doesn't work

When I push the power button, the leds lid up, and that's all, no HDD activity.

I have to force a power-off and start the machine again.

What might be the reason ? What can I do ?
To get some background on the suspend/resume issue with the D600, have a look at this bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/559163]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/559163"). Apparently there are two fixes/workarounds:
1. set a boot password in bios. This will force the video card to initialize during the resume process. Unfortunately, you'll have to enter a password all the time.
2. Use the "radeon.modeset=0" kernel parameter.

> Further, when I do a hibernate, I get an error that I'm not authorized.Hibernate is disabled by default in 12.04. To re-enable, see this link: [http://askubuntu.com/questions/94754/how-to-enable-hibernation-in-12-04]("http://askubuntu.com/questions/94754/how-to-enable-hibernation-in-12-04")

---

### Post by wquatan on 2012-08-20
Sorry I couldn't get back earlier

I tried both options, but unfortunatly none works :-(

1. Suspending en resuming seems to work at first sight, but a couple of minutes after resuming the laptop freezes completely. Same behaveour w/wo docking station.

2. When the parameter is set, it's no longer possible to suspend (= nothing happens)

Actually I didn't look into the hibernate solution.

---

### Post by Toz on 2012-08-20
You may wish to follow the progress of the bug report and add your results to the list.

---

