---
title: "Nvidia resolution problems"
date: 2007-10-12
forum: Desktop Effects &amp; Customization
---

### Post by acl123 on 2007-10-12
Hi,
If I run nvidia-settings I can change the screen resolution to 60Hz, which is what I want. However, under System->Preferences->Screen Resolution in Gnome the resolution says it is set to 52Hz and the maximum I can select is 55Hz.
What is going on?

I have Ubuntu 7.04, GEForce 7300 GS, ViewSonic VG2021m.

---

### Post by yabbadabbadont on 2007-10-12
The nvidia-settings numbers are correct, the gnome ones are not.  Apparently, the driver doesn't report the correct numbers to the gnome settings application.  There are threads about it somewhere here in the forums if you care to search for them.  Not sure what search terms to use though, so it may not be easy to find them.

---

### Post by FuturePilot on 2007-10-12
Yeah, that's a bug. I think, if you want to call it that. Go by what the Nvidia settings are saying. The Gnome one lies:p

---

### Post by acl123 on 2007-10-14
Hi, thanks,
I've found that the Restricted Device Manager is also buggy or at least not doing what I would expect.

It says that Nvidia accelerated graphics is In Use, although not enabled...  Obviously something is wrong there.

I've found that by trying to enable or disable accelerated graphics using the Restricted Device Manager causes all types of crazy troubles.

---

### Post by 1/0 on 2007-10-19
I have the same thing in Kubuntu with a Nvidia 7600 GS and a 19" CRT.

---

