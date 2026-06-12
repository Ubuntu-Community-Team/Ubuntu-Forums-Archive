---
title: "logitech V470 mouse"
date: 2010-06-26
forum: Desktop Environments
---

### Post by RogerTa on 2010-06-26
Hi all,

I am using a [logitech V470 BT mouse]("http://www.logitech.com/en-ca/mice_pointers/mice/devices/3287") with my ubuntu 9.10 desktop system.  This system has no built-in BT, so I am using the BT-USB dongle that came with the[ logitech diNovo Edge keyboard]("http://www.logitech.com/en-ca/keyboards/keyboard/devices/192") that I am also using with this system.

The keyboard works fine, and connecting the mouse to the dongle went smoothly.  However, there is noticeable lag in the cursor movement when using the mouse.

I've experimented with the mouse settings, I've moved the dongle closer to the mouse, and both have improved the situation.  But some noticeable lag remains.

After much experimentation, I've noticed that the remaining lag occurs when I move the mouse after it has not been used for a little while.  It seems the mouse goes to sleep (likely to save batteries) and there is a noticeable delay as it wakes up.  Once its awake, there is no lag.

Does anyone know how to control the sleep behaviour of this mouse, or where I can find such information?  I sent an email to logitech support but have not received an answer yet.

Thanks.

---

### Post by cabez0n on 2011-08-30
Looks like this post if from awhile back but I am also experiencing the same behaviour on ubuntu 11.04 with the same mouse.

I notice the lag when mouse comes from sleep but what bothers me the most is the constant lag, it doesn't feel as good as any other wireless logitech mouse.

I wonder if there is any settings to change regarding polling interval or anything that can be tweaked to get better performance.

---

### Post by pjd99 on 2011-08-31
I find it (the V470) generally a bit laggier than a wired mouse, and it really struggles when the video card is working hard. 

Probably something to do with the internal BT receiver sharing an IRQ with the video card, and running compiz probably doesn't help.

A wireless mouse with its own receiver seems to do better, my guess is that the proprietary receivers poll more often than BT does, and the system just sees these type the same way they see a wired USB mouse.

---

