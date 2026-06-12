---
title: "Ubuntu seems to be quite the battery hog..."
date: 2009-05-23
forum: General Help
---

### Post by cody7002002 on 2009-05-23
Since I switched from windows xp to ubuntu NBR i've found that i'm charging my battery a lot more. I thought ubuntu was supposed to be lighter and better on the battery than xp so why does it seem like the oppoiste?

Is there anything I can do to conserve battery power?

---

### Post by jamesobooth on 2009-05-23
Noticed that on mine as well but I figured it's because my fan is running a lot more and the laptop seems to run a lot hotter.

---

### Post by cody7002002 on 2009-05-23
yeah I've noticed that but is there anything I can do to make the battery life a little better?

---

### Post by Legace on 2009-05-23
> **cody7002002 said:**
> yeah I've noticed that but is there anything I can do to make the battery life a little better?

Read this through: [http://www.phoronix.com/scan.php?page=article&item=ubuntu_battery_life&num=2](http://www.phoronix.com/scan.php?page=article&item=ubuntu_battery_life&num=2)

---

### Post by cody7002002 on 2009-05-25
Maybe it's just me but that guide seems pretty confusing. So just installing powerTOP should help?

---

### Post by sloggerkhan on 2009-05-25
Pretty much you need to find a tweak guide for your model netbook and follow it. Out of the box, Ubuntu tends to have a lot of 'wakeups per second' as shown through powerTop. If tweaked, you can get ubuntu down to 20 or fewer wakeups per second, which will extend battery life drastically, as out of the box Ubuntu often has over 100 wakeups/second.

Additionally, there is the question of LPIA architecture or not. See: [http://www.phoronix.com/scan.php?page=article&item=ubuntu_power_usage&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_power_usage&num=1)

---

### Post by cody7002002 on 2009-05-25
Could you explain to me what "wakeups" are and how one goes about tweaking

---

### Post by cody7002002 on 2009-05-25
ok so I installed powerTOP and read a guide on how to use/read it. 

It says I have 175.3 wakeups per second

The top cause of my wakeups says
36.7% (41.0)  <interrupt> : uhci_hcd:usb3, ath
28.2% (30.0)  Xorg : schedule_hrtimeout_range (hrtimer_wakeup)

at the bottom one of the suggestions is "enable usb autosuspend by pressing the U key or adding usbcore.autosuspend=1 to the kernel command line in the grub config"

What does autosuspend do? and what does adding that line to the kernel do?

---

