---
title: "Can't boot into high graphics mode"
date: 2009-02-04
forum: General Help
---

### Post by DoogleSmile on 2009-02-04
Hi everybody.
I've had Ubuntu running fine on my PC for a few weeks now, but on Sunday I went to boot up, got to the enter password screen then it went to a full screen terminal and didn't load the gui properly.

When I managed to get it to load the gui it wouldn't let me load with full graphics enabled. Is there anything I can try to get this working properly again?

---

### Post by linux_tech on 2009-02-04
what are the computer specs?  Graphics card?
Have you installed the graphics card drivers yet?

---

### Post by mb_webguy on 2009-02-04
You probably need to install a proprietary driver for your video card, but we can't tell you without some more information about your system -- especially your graphics card.

If you install the package sysinfo, it will make it easier to get this information.

---

### Post by DoogleSmile on 2009-02-04
I'm using a Geforce GTX280 but until I tried it on Sunday it was working perfectly. I'd installed the 180.22 64bit linux drivers from Nvidia and had all the fancy windows effects working and resolution at 1920*1200. But now I can't have a resolution higher than 1280*768 when I manage to get the gui to load.

edit:
I've just booted up in Ubuntu and the low graphics mode came up straight away this time without me having to click loads of buttons and stuff. I've just noticed I don't have any sound anymore either.

Would removing then reinstalling the drivers fix these problems?

---

### Post by johnl on 2009-02-04
Did you install the nvidia 180.22 driver from the nvidia website using the nvidia installer?  (I don't think 180.22 is available yet from the repos).  If that is the case, what probably happened is that your kernel got updated since you installed the driver.  When you restarted, the new kernel got used. Since the nvidia driver has to be specifically compiled for your running kernel, it's throwing a fit.

Probably the easiest way to fix it is to re-run the nvidia installer, although be aware that when you install the driver like this it is going to break after every kernel update.

---

### Post by DoogleSmile on 2009-02-04
Ah right, that'll probably explain the Xfi sound card not working again too :(
I'll try reinstalling them then :)

Thanks

Edit:
I've reinstalled both my sound and graphics now and they're both working fine... Thanks for helping :)

---

