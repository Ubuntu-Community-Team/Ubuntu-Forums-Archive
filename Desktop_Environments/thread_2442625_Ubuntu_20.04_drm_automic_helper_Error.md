---
title: "Ubuntu 20.04 drm automic helper Error"
date: 2020-05-05
forum: Desktop Environments
---

### Post by slkamath on 2020-05-05
Hi All,

Hope you are good & safe.

I was previously using Ubuntu 18.04 & couple of days back tried upgrafing to 20.04 & laptop got crash.

Tried installing the fresh 20.04 no luck, so tried 18.04 & 16.04 but no luck. Changed the Hard Drive still no luck. Getting below message. So can anyone help me to solve this issue.

So please find the attached screenshot for your reference.

I am using Lenovo T530 Laptop.

---

### Post by CelticWarrior on 2020-05-05
> I am using Lenovo T530 Laptop
which has Intel+Nvidia Graphics (Optimus).

So, you need to boot and install in UEFI mode with Secure Boot disabled and select the option to install third-party drivers, etc. (Ubuntu 20.04 only; previous still supported releases require those drivers to be installed after). You may need to boot with the additional boot parameter 'nomodeset'.
That should be all, no HDD change unless defective. What you're showing is actually the graphical environment not booting and misinterpreting the last message as the cause. It isn't, those messages are very likely innocuous, unrelated and were there all along, you just didn't notice them until now because the splash screen obfuscated it.

---

### Post by slkamath on 2020-05-05
Thank you so much I will try with UEFI Mode.

This is nearly 5 years old. So dont remember which graphics card. Sorry.

Lokesh Kamath

---

