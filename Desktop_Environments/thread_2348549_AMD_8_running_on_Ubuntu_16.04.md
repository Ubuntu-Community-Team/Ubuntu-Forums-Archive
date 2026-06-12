---
title: "AMD 8 running on Ubuntu 16.04"
date: 2017-01-04
forum: Desktop Environments
---

### Post by deepakdeshp on 2017-01-04
Hello,
Will AMD A8-7410 processor be supported for ubuntu 16..04 fglrx drivers?Do I have to downgrade Ubuntu to get the AMD a8 driver? Which version does the Ubuntu sulport the. Amd A8 driver?Is there any estimated time period when this cpu will be supported in future ubuntu versions?
Thank you for your attention.

---

### Post by QIII on 2017-01-04
Hello!

For 16.04 and beyond, AMD no longer supports fglrx.  They will not be updating it to work with the more recent X Server used by Ubuntu from that release forward.  AMD is responsible for the maintenance and development of the driver, not Canonical.  So it's not a matter of whether any version of Ubuntu supports the AMD driver.  It's the other way around.

When you install 16.04, the installer determines which of two open-source drivers are appropriate:  Radeon or AMDGPU.  I thing yours is supported only by Radeon at the moment.

Some GPUs will also work with the AMDGPU-PRO driver, which is AMDGPU with a proprietary overlay.  But it currently works with a limited number of AMD GPUs.

Support will eventually come for many GPUs back to the HD 7000 series, but which ones is anyone's guess right now.  I made a stab at what looks like it might possibly eventually be supported [here]("http://theleftcoastgeek.net/index.php/categories/12-possible-amdgpu-pro-supported-gpus-by-the-end").  But I can't speak for AMD.

The upshot of all of this is that you would probably be better of running 14.04 or 14.04.1 with the fglrx driver.  14.04.2 and forward have graphics stacks and HWEs that might be a problem -- and some of which are not even supported any longer.

Sorry for the bad news, but AMD is in the middle of doing what the open source community asked for:  helping in the development of a good open source driver.

---

### Post by deepakdeshp on 2017-01-05
Thank you.It is indeed bad news. Intel looks to be the platform one should go with.
I found this on Mint forum
[https://forums.linuxmint.com/viewtopic.php?p=1215142#p1215142](https://forums.linuxmint.com/viewtopic.php?p=1215142#p1215142)
What applies to Mint 18 should be good for Ubuntu 16.04?

---

