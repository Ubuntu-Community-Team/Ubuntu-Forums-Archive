---
title: "AMD Unsupported Hardware"
date: 2013-05-04
forum: Gaming &amp; Leisure
---

### Post by Extol11 on 2013-05-04
So I just installed Lubuntu 13.06 on my desktop about an hour ago. I got install the amd drivers and it has this constant watermark on the lower right that says "AMD unsupporte hardware" on the lower right. I have a Radeon HD 6790. I just want to know if I should be worried about this or not. I just migrated from a 4870 because AMD dropped support for it after Ubuntu 12.04 LTS. What does unsupported hardware mean? How can I stop that icon from showing (it's rather annoying). Any help will be greatly appreciated.

---

### Post by bcschmerker on 2013-05-04
Ironic!  As it turns out, [Advanced Micro Devices®]("http://www.amd.com/") is concentrating on late-model Radeon® HD™ series, e.g. your new 6000 Series, for its proprietary apps for Ubuntu® (packages: fglrx, fglrx-amdcccle).  The [X Organization]("http://www.x.org/") has taken up support for the older Radeon® and Radeon® HD™ series in the form of an open-source video driver (package: xserver-xorg-video-radeon) which can handle multiple displays on a single GPU; I have had no issues on the planar Radeon® HD™ 3200 in my own hot-rod LinUX box.

---

### Post by R33D3M33R on 2013-05-05
Solution is here: [http://ubuntuforums.org/showthread.php?t=2074962](http://ubuntuforums.org/showthread.php?t=2074962)
Just copy&paste the string to the right file.

---

### Post by Extol11 on 2013-05-05
> **R33D3M33R said:**
> Solution is here: [http://ubuntuforums.org/showthread.php?t=2074962](http://ubuntuforums.org/showthread.php?t=2074962)
Just copy&paste the string to the right file.

Thanks a lot. I'll get into that. The driver seems to be working fine anyways. It plays Trine 2 just perfectly, it just keeps that watermark on at all times.

---

### Post by holastickboy on 2013-05-05
This watermark has been really annoying, they should sticky the fix in this forum.

---

### Post by Extol11 on 2013-05-07
That signature did not remove the watermark for me. Is there any other thing I can try?

---

### Post by R33D3M33R on 2013-05-08
You should copy&paste carefully. There might be a space before or after the string which can cause the check to fail. Also, double check it really saved and don't forget to reboot. I tried this on three betas and it always worked.

---

