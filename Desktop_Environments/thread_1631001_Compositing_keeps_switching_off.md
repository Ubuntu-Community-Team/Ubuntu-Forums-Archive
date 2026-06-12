---
title: "Compositing keeps switching off?"
date: 2010-11-26
forum: Desktop Environments
---

### Post by carlbeech on 2010-11-26
Hi Forum,

I'm running kubuntu, 10.10, 64 bit on my ASUS X59GL, with 4Gb ram - and NVIDIA on board GeForce 8200m.

I'm running KDE with compositing switched on - trouble is that it keeps saying Desktop effects are too slow and compositing is suspended.

Surely this setup is powerful enough - this seems to be getting worse with each subsequent release - (a couple of releases ago, this didn't happen).

It's just happened again, and all I'm running is Firefox, nautilus, skype and dropbox (all but firefox are minimised), and uptime load average is .3

Is anyone else experiencing this problem?

Is there any 'ratings' as to how 'expensive' each of the effects are? - i.e. which are the least impact, and which are the most?

Many thanks

Carl.

---

### Post by grege on 2010-11-26
Assuming your desktop effects work properly most of the time then .....

Go into System Settings -> Desktop Effects -> Advanced and select "Disable functionality checks"

If desktop effects never work then I would not try this option or you may not be able to get back to your desktop.

I have a Radeon HD4290 and I have to select this to stop the system turning off effects at every boot.

---

### Post by MaDxCrEaM on 2010-12-02
> **grege said:**
> Assuming your desktop effects work properly most of the time then .....

Go into System Settings -> Desktop Effects -> Advanced and select "Disable functionality checks"

If desktop effects never work then I would not try this option or you may not be able to get back to your desktop.

I have a Radeon HD4290 and I have to select this to stop the system turning off effects at every boot.

Thanks. I had same problem. Your trick worked for me. BTW I have an ATI HD 5770.

---

### Post by inobe on 2010-12-02
> **carlbeech said:**
> Hi Forum,

I'm running kubuntu, 10.10, 64 bit on my ASUS X59GL, with 4Gb ram - and NVIDIA on board GeForce 8200m.

I'm running KDE with compositing switched on - trouble is that it keeps saying Desktop effects are too slow and compositing is suspended.

Surely this setup is powerful enough - this seems to be getting worse with each subsequent release - (a couple of releases ago, this didn't happen).

It's just happened again, and all I'm running is Firefox, nautilus, skype and dropbox (all but firefox are minimised), and uptime load average is .3

Is anyone else experiencing this problem?

Is there any 'ratings' as to how 'expensive' each of the effects are? - i.e. which are the least impact, and which are the most?

Many thanks

Carl.

you failed to provide information whether or not you activated the nvidia driver or if your using the opensource driver.

you need to activate the nvidia proprietary driver.

---

