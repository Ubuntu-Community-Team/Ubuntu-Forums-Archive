---
title: "Safe to disable udev...?"
date: 2009-01-27
forum: General Help
---

### Post by icanfly0307 on 2009-01-27
Hi,
   I'm optimizing my system's boot time. I have a Vaio Laptop and I was wondering if it would be safe to remove udev from the startup processes? From wikipedia, I found that it detects hardware changes during startup. I never change my hardware and I don't add any new devices to it, so would it be safe to remove it from startup? Thanks... :)

---

### Post by sdennie on 2009-01-27
It's not safe to remove it unless you manually load each module that you need for startup.  Your machine won't boot without either udev or manually loading the modules and manually loading them is a bit risky.  Rather than removing udev, I would recommend looking at this guide instead: [http://wiki.archlinux.org/index.php/Speedup_udev](http://wiki.archlinux.org/index.php/Speedup_udev).  Be prepared for the possibility of making your machine unbootable regardless of what route you take.

---

### Post by icanfly0307 on 2009-01-27
Okay, thanks. I have Windows XP alongside Ubuntu, so I'll still be able to fix Ubuntu if I mess up.

---

### Post by adamlau on 2009-01-27
You should be good to go as long as you have HAL up and running. Only way to find out is to disable udev and use your box as you normally would, keeping an eye out for anomalies and the like. I have udev disabled across five out of six boxes (left it enabled on VectorLinux) with no ill effects through usage, or visible via system logs.

---

### Post by icanfly0307 on 2009-01-27
Oh, and btw, I also read on google that devfs is a faster alternative to udev. Would it work in Ubuntu? Thanks again. :)

---

### Post by dcstar on 2009-01-27
> **adamlau said:**
> You should be good to go as long as you have HAL up and running. Only way to find out is to disbale udev and use your box as you normally would, keeping an eye out for anomalies and the like. I have udev disabled across five out of six boxes (left it enabled on VectorLinux) with no ill effects through usage, or visible via system logs.

I assume it comes into play with external devices like USB drives/mice/keyboards etc, so as long as these don't change then it may well be "unnecessary".

---

### Post by icanfly0307 on 2009-01-27
Thanks guys! I'm on a laptop so I assume nothing will get messed up. I'll take your word for it and experiment. Would disabling udev from sysv-rc-conf be the right way to do it? Thanks again! :)

---

### Post by icanfly0307 on 2009-01-27
Whew! I disabled udev and my X and touchpad didn't work. So I logged in from a tty and fixed udev. :sigh:... It was so cool to look at my computer boot in 10 seconds for once. I wish I could've kept it that way...

Anyways, thanks for your help everyone...

---

