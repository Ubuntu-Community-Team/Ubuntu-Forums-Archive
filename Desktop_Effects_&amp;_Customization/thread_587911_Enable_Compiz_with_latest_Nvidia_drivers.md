---
title: "Enable Compiz with latest Nvidia drivers"
date: 2007-10-23
forum: Desktop Effects &amp; Customization
---

### Post by BrownieBoy on 2007-10-23
I have the latest Nvidia graphics driver installed from their web site; i.e., *not* the ones installed by Gutsy's Restricted Drivers Manager tool.  My problem is that I can't enable Desktop Effects via System->Preferences->Appearance.  When I try to do so, it tells me that the Nvidia driver isn't enabled (not true) and then begins to install the nvidia_new driver.  As I understand it, this driver is actually older than the driver that I've already installed from Nvidia's web site.

So, my question is, is there an easy way to enable Desktop Effects for my situation?  I know that I can type "compiz --replace" in a terminal, but that's a bit of a pain; especially as I then have to keep that terminal open to keep compiz enabled.

My graphics card is an 8800 GTS by the way.

---

### Post by Nunu on 2007-10-23
as far as i know you need the nvidia-new driver, please correct me if i am wrong. have you tried that driver before or have you had problems with it?

---

### Post by BrownieBoy on 2007-10-23
Yes, I did.  And it worked, and Compiz was fine.  But, I couldn't get it do Direct Rendering - i.e, gxlinfo always showed "Direct rendering = No".  That's why I went back to the driver on the Nvidia site.  But then, I couldn't get *that* driver to do Direct Rendering either, initially.  Typeing "sudo apt-get remove xserver-xgl" at a Terminal session fixed that (and would probably have done so for the nvidia_new driver too, if I'd known.

I read somewhere that the Restricted Drivers Manager doesn't work with re-compiled kernels, and I 'm pretty sure that I had to re-compile mine to get the latest driver installed.

---

