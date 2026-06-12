---
title: "Possible to run beryl using an ATI Radeon 9200?"
date: 2007-03-26
forum: Desktop Effects &amp; Customization
---

### Post by ryguy9090 on 2007-03-26
Ubuntu newb here...

Installed beryl without a hitch, but as soon as I clicked on the beryl icon everything locked up.
My initial thought is the problem lies in my drivers or the video card itself, as it's a somewhat older card. I believe I installed the latest drivers already via EasyUbuntu? Just wanted to make sure the hardware itself isn't the problem before I spend too much time messing with the drivers.
Is there any sort of list of supported video cards?

Thanks!

---

### Post by Waappu on 2007-03-26
Hi

I didn't get my card working with official driver "fglrx" but open source driver works great and even better with Xorg 7.2

Read this thread. I'm not sure this works with your card. Use with own risk.
[http://ubuntuforums.org/showthread.php?t=338771](http://ubuntuforums.org/showthread.php?t=338771)

---

### Post by teryan2006 on 2007-03-27
Your radeon 9200 will definitely work with beryl. I think you installed the fglrx driver with EasyUbuntu, so you will need to configure XGL to work. However, the 9200 is supported by the xorg driver and works with AIGLX. For a newb, i think that's a little bit easier to setup.

---

