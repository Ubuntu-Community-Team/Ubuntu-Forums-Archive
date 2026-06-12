---
title: "System freezes after suspend"
date: 2012-08-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by emagar on 2012-08-02
I am running the sputnik [release/]("http://hwe.ubuntu.com/uds-q/dellxps/") of Ubuntu 12.04 on a Dell xps13 i5core. When I close the laptop, it will most likely not re-awaken when I re-open it. Just a blank screen with a flashing cursor. 

It will not react to CTRL-ALT-DEL. CTRL-ALT-F1 will open a shell, but the system will not allow a reboot or a shutdown.

Pushing the off button --- sweating cold! --- is all that I have been able to resuscitate the machine.

I gave the swap partition 4GB, which is the size of the RAM in the machine, I believe. Yet this should not be the problem --- swap is used for hibernate but not for suspend, right?

Any advice will be highly appreciated.

---

### Post by Toz on 2012-08-07
> **emagar said:**
> I am running the sputnik [release/]("http://hwe.ubuntu.com/uds-q/dellxps/") of Ubuntu 12.04 on a Dell xps13 i5core. When I close the laptop, it will most likely not re-awaken when I re-open it. Just a blank screen with a flashing cursor. 

It will not react to CTRL-ALT-DEL. CTRL-ALT-F1 will open a shell, but the system will not allow a reboot or a shutdown.

Pushing the off button --- sweating cold! --- is all that I have been able to resuscitate the machine.

I gave the swap partition 4GB, which is the size of the RAM in the machine, I believe. Yet this should not be the problem --- swap is used for hibernate but not for suspend, right?
Correct.

> Any advice will be highly appreciated.
I notice by looking at the specs that it has a usb 3.0 port. You might want to try this fix: [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug").

---

### Post by emagar on 2012-08-08
> **Toz said:**
> I notice by looking at the specs that it has a usb 3.0 port. You might want to try this fix: [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug).

Thanks again Toz, I've added the usb3 fix. I'll monitor the system and report soon if SOLVED. 

The post also hints that my swap may be too small (it has the same size as my RAM). I'll double it, just in case. But, if I am understanding Ubuntu operation correctly, this should have no impact on suspend...

---

### Post by Toz on 2012-08-08
That is correct. A swap partition is not required for suspend. It is required for hibernate.

---

### Post by gerrman97 on 2012-10-22
check problem with vid card. or drivers for the video card.

---

