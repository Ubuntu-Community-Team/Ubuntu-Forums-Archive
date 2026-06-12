---
title: "Monitor or Video Issue? Resultion Issue."
date: 2010-03-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Quarum on 2010-03-22
I am having issues with a clean install of Ubuntu 9.10 on my Dell Inspiron 530. Only resolutions available are 640x480 and 800x600.

I have read a lot of the forums but unsure exactly how to proceed. The monitor is not being detected in 9.10.

I have installed all updates and tried the "sudo apt-get install xserver-xorg-video-intel" and it reports they are installed and current.

Here is more info on the computer. Please let me know what additional you might need and I will happily get the info together.

Computer: Dell Inspiron 530

Video: Integrated Intel Graphics Media Accelerator 3100

Monitor: 21" Gateway VX100 (Using the BNC Style connectors)

4g RAM

Ubuntu 9.10

2 Resolutions 800x600 and 640x480 only 60Hz

1600x1200 is max resolution of the monitor

Any/all help is greatly appreciated. Thanks everyone and have a great day!

Quarum

---

### Post by Grenage on 2010-03-22
I have a 9.10 xorg guide [here]("http://www.grenage.com/xorg.html"), does it help at all?

---

### Post by Quarum on 2010-03-22
> **Grenage said:**
> I have a 9.10 xorg guide [here]("http://www.grenage.com/xorg.html"), does it help at all?

Not much - I am new to Ubuntu and this is a bit above my level right now. Sorry

---

### Post by Quarum on 2010-03-22
Let me ask this - is the issue because Ubuntu is not seeing the monitor? I hit the Detect and it is not detecting the monitor. Is this because of an older monitor? Would I solve my problems by possibly switching out the monitor?

---

### Post by Grenage on 2010-03-22
In my experience, it's because Ubuntu isn't receiving the EDID data - that's usually down to the monitor or cable.  A different monitor could well fix it, but you _should_ be able to get it working with a custom xorg.conf.

---

### Post by Quarum on 2010-03-22
I put a different monitor on it and rebooted and the monitor was detected and the display options are all there.

Thanks for your help! I really appreciate it.  :)

---

### Post by Grenage on 2010-03-23
Glad you got it sorted!

---

