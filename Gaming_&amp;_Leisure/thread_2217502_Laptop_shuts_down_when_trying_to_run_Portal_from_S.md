---
title: "Laptop shuts down when trying to run Portal from Steam"
date: 2014-04-17
forum: Gaming &amp; Leisure
---

### Post by hst19 on 2014-04-17
I've been trying to run Portal from the native Steam client and every time the laptop shuts down after a minute or so. I came across some info while searching for a solution. I'm new to linux so can someone tell me if I can safely reproduce the steps shown in this link in Ubuntu (12.04) and might it help?

[https://bbs.archlinux.org/viewtopic.php?pid=1326090#p1326090](https://bbs.archlinux.org/viewtopic.php?pid=1326090#p1326090)

My specs:
Ubuntu 12.04 (kernel 3.11)
Intel core i3 @ 2.4 GHz
Nvidia GT 335M (Nvidia driver 331 installed) with bumblebee 3.2 
2 GB RAM

I hope there's no rule against linking to another forum..I really need some help here.

---

### Post by oldrocker99 on 2014-04-17
That link points to someone who is not using the nVidia 331 driver. Your laptop should be able to run Portal with no difficulty, so it is probably something else. Some laptops shut down when they're overheating; is your properly ventilated?

---

### Post by hst19 on 2014-04-17
Thanks for the reply, and I don't think there's a ventilation problem. I was using Windows until recently and I could play "heavy" games without shutdown, and right now there's no loud fan noise or hotness during normal use.

---

### Post by oldrocker99 on 2014-04-18
I just reread your original post, and, if you have Bumblebee, you should remove it; yours is not an Optimus GPU. This **may** be the source of your problem.

---

### Post by hst19 on 2014-04-18
> **oldrocker99 said:**
> I just reread your original post, and, if you have Bumblebee, you should remove it; yours is not an Optimus GPU. This **may** be the source of your problem.

Thanks for pointing that out! Apparently my GPU uses Hybrid SLI hybrid power technology..is there any way I can get this to work in ubuntu?

---

### Post by oldrocker99 on 2014-04-18
A bit of Googling found this:
[http://ieatbinary.com/2010/02/21/configuring-linux-to-work-with-nvidia-hybrid-sli-technology/](http://ieatbinary.com/2010/02/21/configuring-linux-to-work-with-nvidia-hybrid-sli-technology/)

Google **is** your friend, especially if you're a GNU/Linux user!

---

### Post by hst19 on 2014-04-18
> **oldrocker99 said:**
> A bit of Googling found this:
[http://ieatbinary.com/2010/02/21/configuring-linux-to-work-with-nvidia-hybrid-sli-technology/](http://ieatbinary.com/2010/02/21/configuring-linux-to-work-with-nvidia-hybrid-sli-technology/)

Google **is** your friend, especially if you're a GNU/Linux user!

Thanks :) and maybe this is a dumb question but can I manually make ubuntu use (or not use) the Nvidia card when I want to by editing the xorg.conf as shown? And my Nvidia card works normally in the normal desktop environment without bumblebee..it just stays on all the time (very loud fan noise) which I guess is what should happen without a "switching" technology.

---

