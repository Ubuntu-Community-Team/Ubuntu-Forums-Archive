---
title: "Compiz fusion installed, however effects still won't run"
date: 2007-12-27
forum: Desktop Effects &amp; Customization
---

### Post by Master-of-None on 2007-12-27
I installed Compiz Fusion, however the desktop effects won't work. I try to enable them, but it says:
```
The Composite extension is not available
```

which means I need to install something, what do you recommend to install? or do I even need to install something at all?

---

### Post by din on 2007-12-27
Hi.
I think to get help you should first : 
post output of "compiz" in terminal
as well as your graphic hardware.

---

### Post by Master-of-None on 2007-12-27
```
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
```

and as for my video card, its:
ATI Radeon Xpress 1150 IG

I have 1Gig of ram
and 2 AMD Turion 64, 1.6gh

---

### Post by Forlong on 2007-12-27
Go to *System &#8594; Administration &#8594; Restricted Drivers Manager * and make sure the driver for your ATI card is enabled.

Then you need to install Xgl:
```
sudo apt-get install xserver-xgl
```
Reboot and see if it worked.

---

### Post by Master-of-None on 2007-12-27
It told me I had the recent version

---

### Post by jean noel on 2007-12-28
> **Forlong said:**
> Go to *System &#8594; Administration &#8594; Restricted Drivers Manager * and make sure the driver for your ATI card is enabled.

Then you need to install Xgl:
```
sudo apt-get install xserver-xgl
```
Reboot and see if it worked.

Absolutely great.
Thank you

---

### Post by Master-of-None on 2007-12-28
Nevermind, it appears it wasn't installed afterall, I thought I tried to install it before and it said it was in though. anyway, thanks. I absolutely love the paint with fire effect :)

---

