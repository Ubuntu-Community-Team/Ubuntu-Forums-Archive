---
title: "High CPU usage from Xorg"
date: 2007-05-31
forum: Desktop Environments
---

### Post by Chaoticwhizz on 2007-05-31
I run Kubuntu 7.04. I have the Nvidia card and am using the 1.0-9755 driver  off the Nvidia website. If I walk away from my computer long enough and then come back Xorg will take all free processor usage. I can  switch to tty1 and reboot the PC. It acts normally again until I let it sit for awhile. I feel it is either linked to the screen saver which I have tried several different ones, or possibly the power saving settings.Other weirdness is if I turn off the power management settings from the System Settings --> Power and Display what will happen is my screen will go blank after 5 min instead of the actual screen saver coming. It does this on standard 2-D scrolling marquee screen saver as well as 3-d ones. I originally installed Edgy Eft and then upgraded to Feisty using Adept. This problem never happened in Edgy and I don't even think it always happened since I have been using Feisty. I tried reinstalling the Nvidia driver with no luck. All 3-d apps run fine. This is the only problem I have.

---

### Post by Chaoticwhizz on 2007-06-07
Fixed by disabling SuperKaramba applets. Launchpad link

[https://bugs.launchpad.net/kdeutils/+bug/109507](https://bugs.launchpad.net/kdeutils/+bug/109507)

---

### Post by vnkatesh on 2007-12-12
thank you for coming back and posting the solution.

---

