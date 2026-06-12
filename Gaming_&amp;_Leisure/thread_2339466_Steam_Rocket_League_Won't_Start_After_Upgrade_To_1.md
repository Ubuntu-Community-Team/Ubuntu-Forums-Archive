---
title: "Steam: Rocket League Won't Start After Upgrade To 16.04 LTS"
date: 2016-10-09
forum: Gaming &amp; Leisure
---

### Post by pc-load-letter on 2016-10-09
I installed Rocket League on Ubuntu 14.04 LTS when it was released on  Linux and it ran great. However, I couldn't use my controller and  decided to upgrade to 16.04 LTS for, among other reasons, Xbox One  controller support. Upon upgrade the Steam client wouldn't even launch  so I followed the solution [here]("http://askubuntu.com/a/771507/594608") and was able to get the Steam client running.

  Unfortunately, now I'm unable to launch Rocket League at all from the Steam Client. I get the "Preparing to launch Rocket League"  window and then nothing. The process just sits there consuming 3.2 MB  of memory. No other games appear to be affected. Using open source  Radeon driver.

Any help would be greatly appreciated, as I don't even know where to begin to resolve this issue. Thanks!

---

### Post by howefield on 2016-10-09
Thread moved to the "*Gaming & Leisure*" for a better fit.

---

### Post by Lance321 on 2016-10-12
Yes, Ubuntu 16.04 will not run Steam client, its broken for some reason. Canonical does't even list it as an available application. I got my client working using the same fix as you did.

However I found switching to the AMD drivers (in Additional Drivers) gave me better support and my games ran better. You could give that a try.

---

### Post by pc-load-letter on 2016-10-12
> **pete-wilkins321 said:**
> Yes, Ubuntu 16.04 will not run Steam client, its broken for some reason. Canonical does't even list it as an available application. I got my client working using the same fix as you did.

However I found switching to the AMD drivers (in Additional Drivers) gave me better support and my games ran better. You could give that a try.

Are you referring to the AMDGPU proprietary blob that sits on top of the new Radeon open source kernel driver? Because I'm using an older GPU that isn't supported by AMD's new proprietary driver. The only thing that appears for me in "Additional Drivers" is the "Using Processor microcode firmware for AMD CPUs from amd64-microcode (proprietary)" option (Which currently isn't selected).

Also, is there any more info regarding the Steam client issue? I see bug reports have been issued on Steam's GitHub for their linux client.

This is the fastest I've upgraded to a new LTS. Usually I wait at least a full year after the official release of an LTS before doing an LTS to LTS upgrade in the hopes that any major bugs have been worked out by the time I upgrade. This is the first time I've thrown caution to the wind with an upgrade, in spite of the warnings that AMD's new drivers aren't ready for prime time. Mainly because I'd been eagerly awaiting many of the features/updates released in 16.04. Looks like I paid the price for it. That said, in spite of the myriad of issues the upgrade caused, this was the first LTS to LTS upgrade that didn't completely brick my system. So I guess that's progress.

---

### Post by QIII on 2016-10-12
Hello!

Just for clarity here:

AMDGPU is not a blob sitting on Radeon.  Both Radeon and AMDGPU are fully open source drivers and they are two separate things.  One or the other is installed when Ubuntu is installed based on the hardware present.  AMDGPU is a product of AMD's cooperation with the open source community (primarily Canonical) to provide a capable and complete driver for AMD's newer generation of GCN hardware.

AMDGPU-Pro is the proprietary binary (all the best goodies) laid on top of the open source AMDGPU base.

AMDGPU and AMDGPU-Pro are working for me.  I have hardware that is supported.  AMDGPU will eventually be extended to work with AMD GPUs as far back as the HD 7000 series.  Earlier models are not compatible.  Thus, Radeon will be used.

AMD has no plans at present to maintain the Linux fglrx driver any longer to keep up with changes to the Linux graphics stack.

---

### Post by pc-load-letter on 2016-10-12
> **QIII said:**
> Hello!

Just for clarity here:

AMDGPU is not a blob sitting on Radeon.  Both Radeon and AMDGPU are fully open source drivers and they are two separate things.  One of the other is installed when Ubuntu is installed based on the hardware present.  AMDGPU is a product of AMD's cooperation with the open source community (primarily Canonical) to provide a capable and complete driver for AMD's newer generation of GCN hardware.

AMDGPU-Pro is the proprietary binary (all the best goodies) laid on top of the open source AMDGPU base.

Thanks for the info! This is by far the clearest explanation I've read yet regarding the new AMD drivers. I've read numerous articles from OMG! Ubuntu!, Softpedia and Phoronix that were either extremely vague (about which drivers they were referring to) and precisely how they worked/differed. My above description was basically the best description I'd read regarding the drivers from an article on the subject months ago.

If the only difference between the Radeon and AMDGPU drivers is the hardware they are designed for, that would make sense, as if I remember correctly their old Catalyst driver had multiple channels, each optimized for what hardware you were using. The new Radeon driver simply being the replacement for the old legacy hardware Catalyst driver.

Will the AMDGPU-Pro proprietary binary code remain proprietary indefinitely, or will parts of it eventually get incorporated into the base AMDGPU open source driver over time? I assume this is just AMD's way of protecting any competitive advantage they have when adding new features to the driver. I'm just curious if any of that code will trickle down to the open source driver over time? Or perhaps I'm still misunderstanding precisely what AMDGPU-Pro is?

I've also been wondering, is this open source Radeon driver included in 16.04 a completely new open source driver for AMD graphics cards? Or was it built upon the old open source driver that was included in previous versions of Ubuntu (the old alternative to the proprietary fglrx)?

---

