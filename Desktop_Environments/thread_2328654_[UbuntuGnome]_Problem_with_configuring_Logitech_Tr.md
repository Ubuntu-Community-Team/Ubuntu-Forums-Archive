---
title: "[UbuntuGnome] Problem with configuring Logitech Trackman Marble mouse in 16.04"
date: 2016-06-23
forum: Desktop Environments
---

### Post by johannesg-s on 2016-06-23
I've used this guide ( [https://help.ubuntu.com/community/Logitech_Marblemouse_USB](https://help.ubuntu.com/community/Logitech_Marblemouse_USB) ) without problems to adjust my Logitech Trackman Marble mouse since 12.04. Allowing me to change the trackball into a scroll wheel if one of the buttons is held down. It has worked fine in pretty much every release of Ubuntu since 12.04, including at the very least Xubuntu, Lubuntu and more. 

But yesterday I upgraded to Ubuntu Gnome 16.04 from Ubuntu 14.04 (Although, I have seperate partitions for /home and /root, so /root was wiped clean. So, in a way it was a clean install) and when I put my 50-marblemouse.conf back into /usr/share/X11/xorg.conf.d/ and restarted it refused to work (in other words, nothing happens). I've tried also copying the examples directly from [https://help.ubuntu.com/community/Logitech_Marblemouse_USB](https://help.ubuntu.com/community/Logitech_Marblemouse_USB) without luck. It's as the system is not reading the file at all.

Does anyone have any idea what might be the problem here?
Is xorg.conf.d files not the supported way of adjusting mouse settings anymore?
Any good way to be able to check if the system is actually reading the file or not?

---

### Post by x-contact-0 on 2016-06-29
I have the exact same problem, except that I installed on a fresh new disk on a new laptop. Xorg seemed to take some settings (logs showed Marblemouse detected with proper settings) but the changes didn't show up in X. Though I haven't tried any other DE than Gnome, so it *could* be just a Gnome-thing.

Eventually got it to work by using 'xinput'. Follow the 'Alternative: apply settings via xinput' instructions on the wiki:

[https://help.ubuntu.com/community/Logitech_Marblemouse_USB#Alternative:_apply_settings_via_xinput](https://help.ubuntu.com/community/Logitech_Marblemouse_USB#Alternative:_apply_settings_via_xinput)

---

