---
title: "Various problems trying to install ubuntu"
date: 2006-01-08
forum: General Help
---

### Post by enderv on 2006-01-08
Hi,
I've finally decided to get a linux distro, and ubuntu looked like a fairly user-friendly. Last time I had linux was about 5 years back, but I was constantly running into HW problems, so I let it go.

Ok, so I downloaded 386 version of the DVD, and went on installing it. I expected to have a problem with wireless, as I did, but I thought I'd have X running out of the box. Not so.. 

It looks like ubuntu cannot figure out my ATI 800XL (PCIe) card. It detects it has a PCI card, but then the last two lines in the log are "ATI Mach PCI64 not detected", followed by "no device detected" error and "no screen". (can't copy paste Xlog, as I can't write to my NTFS partition - how can I mount a USB flash drive?)

I tried the various Wiki links around, but it seems that fglrx is not on the DVD distro? At least apt cannot find it anywhere...
Thanks,
Vlad

---

### Post by Thirsteh on 2006-01-08
Try following the guide for ATI drivers in Linux even though you don't have a graphical interface, and see if you can get X to start with those drivers. I've never worked with ATI in Linux so I apologize for not being able to help you further.

---

### Post by enderv on 2006-01-08
[QUOTE=Thirsteh]Try following the guide for ATI drivers in Linux even though you don't have a graphical interface, and see if you can get X to start with those drivers. I've never worked with ATI in Linux so I apologize for not being able to help you further.[/QUOTE]
Well, that's what I tried, but the problem was that there wasn't fxglr package anywhere (or didn't seem to) - I was just getting E: not known or something like that from apt-get.

In the end, I've installed the drivers from ATI, which seems to work (although I had to configure them with ATI's config - the xorg didn't seem to notice fglrx was installed and still had just ati there). My process was slightly different from what WIKI was suggesting - I beeded libstdc++5 (and thus gcc3.3.base) and could do it w/o module assistant.

At least that's the graphics done, now need to move on my USB wireless :)

---

