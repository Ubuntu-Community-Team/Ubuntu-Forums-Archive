---
title: "[SOLVED] &amp;quot;Desktop effects could not be enabled&amp;quot;?"
date: 2008-03-28
forum: Desktop Effects &amp; Customization
---

### Post by nappymonster on 2008-03-28
Hi all,
When i set the desktop effects to anything but "None" i get a "Desktop effects could not be enabled" error :(

My specs are:
Running from external hard drive (though i get same error from live CD)
Computer: Samsung X50
Type: laptop
Ram: 1GB Of Ram
Motherboard:
-Manufacturer: Samsung Electronics
-Model: SX50S Revision MP
BIOS: Phoenix Technologies LTD
-Version 11ZA
cpu:
-Intel Pentium M 740
1.73ghz
MMX, SSE, SSE2

Thanks,
Nappymonster

---

### Post by jan quark on 2008-03-28
what is your graphic card?
did you install the drivers for it successfully?

if it is a ati you can try this small guide:

[http://ubuntuhelp.piranho.de/xserver.html](http://ubuntuhelp.piranho.de/xserver.html)

---

### Post by nappymonster on 2008-03-28
Thanks! Erm...
Graphics card, not sure, but will try and find out.
Just seen in the top it said "restricted drivers available". I clicked on it and have two options:
ATI accelerated graphics driver
Software Modem driver

Both have a red traffic light and are "Not in use". Is it OK to install them?

---

### Post by jan quark on 2008-03-28
to detect your hardware or your graphic card run this in terminal
```

lspci

sudo lshw
```

for me the restricted drivers for my ati worked fine so... I would install them and then proceed how I explained in the guide

edit:
I hope you have a working internet connection

---

### Post by nappymonster on 2008-03-28
Thanks! 
My Graphics card is a Radeon Mobility X600
But!...
1) when i select anything but none, i get:
"The Composite extension is not available"

thanks,
Nappymonster

---

### Post by Waappu on 2008-03-28
Hi

You need install restricted driver and use XGL.

See this guide
[http://ubuntuforums.org/showthread.php?t=580748&highlight=xgl](http://ubuntuforums.org/showthread.php?t=580748&highlight=xgl)

---

### Post by nappymonster on 2008-03-28
Thank you very much - it's now working!

---

