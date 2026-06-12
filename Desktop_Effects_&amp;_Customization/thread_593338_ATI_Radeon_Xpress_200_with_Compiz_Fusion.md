---
title: "ATI Radeon Xpress 200 with Compiz Fusion"
date: 2007-10-27
forum: Desktop Effects &amp; Customization
---

### Post by bipinchandra2n on 2007-10-27
Hello Friends,

I have AMD 64 bit CPU, MSI mother board with ATI Radeon Xpress 200 RS482 on board graphics, I just wanted to check whether installing Ubuntu 7.10 (Gutsy Gibbon) will directly enable compiz fusion and this eye candy will be working just right out of the box or I have to do some work arounds in order to make it work. Since I am a newbie any help would be appreciated.

Thank you:)

---

### Post by SigmundL on 2007-10-27
I had problems with that setup, still no xgl and thus no compiz (3D effects)...

/S

---

### Post by Jay_Davis on 2007-10-27
Desktop effects were not enabled by default in 7.10 when I installed it on my Acer Aspire 5100, also with the 200m graphics. You can either install xserver-xgl and it will configure the XGL session and set that to default or you can install the new ATI drivers. Both of of these ways have stability problems, but using XGL is much faster than the ATI drivers. This is a really poor piece of graphics hardware when it comes to Linux compatibility I'm afraid. I ended up having to put XP back on that laptop, and even Vista performs better than 7.10 at the moment (which shows how much room there is for improvement, I expect performance and stability under Linux to surpass Windows in the future). This may change now that ATI seems to be working on better support for their Linux users, but for right now there's not much you can do :(

Good luck with your setup.

---

### Post by jimerickso on 2007-10-27
istall the new fglrx 8.42.3 driver and you will not need xgl.

---

### Post by Melcar on 2007-10-27
Install the new 8.42 drivers.  A few extra tweaks and you can get Compiz working.  Unfortunately, AIGLX implementation with these drivers seems a bit buggy and with that weak IGP you will suffer.  I'm currently running Compiz on my Compaq laptop with a x200 chip and the new drivers, and while performance is not that bad, it may end up annoying you at the end.  XGL seems to run much better at this point.  Keep in mind that almost all my issues with this driver are with Compiz; everything else runs fine.

---

### Post by motang on 2007-10-27
> **bipinchandra2n said:**
> Hello Friends,

I have AMD 64 bit CPU, MSI mother board with ATI Radeon Xpress 200 RS482 on board graphics, I just wanted to check whether installing Ubuntu 7.10 (Gutsy Gibbon) will directly enable compiz fusion and this eye candy will be working just right out of the box or I have to do some work arounds in order to make it work. Since I am a newbie any help would be appreciated.

Thank you:)

Well I was **very** happy today as I followed this [tutorial]("http://ubuntu1501.blogspot.com/2007/08/compiz-fusion-in-fiesty-with-xgl.html") and got XGL working on my HP dv2000z laptop which also has ATi Radeon Xpress 200M.  Hope it works out for you.

**[COLOR="Red"]Note[/COLOR]**: But be careful and make sure that you have all your important stuff backed in case something goes wrong.

---

