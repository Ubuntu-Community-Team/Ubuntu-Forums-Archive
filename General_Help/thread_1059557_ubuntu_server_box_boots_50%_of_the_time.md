---
title: "ubuntu server box boots 50% of the time"
date: 2009-02-03
forum: General Help
---

### Post by jimmy the saint on 2009-02-03
I have an ubuntu server box that won't boot without the irqpoll option for some reason.  It kicks out an error about irq 18 and something or other.  The box is headless, so I cannot monitor the boot process, which makes this issue even more irritating.

Essentially, every other time I have to reboot the thing for whatever reason (the latest was a new HDD addition) it doesn't boot all the way and become available to the network, requiring a hard power down.  I hate doing that because I know it isn't good for it.  Without pulling it out and attaching a monitor to it and powering it on and off a few times, does anyone have a likely culprit?  its a dell vostro 200 box.

I know it's not the best form to ask for help without first gathering the requisite data, but pulling it out and connecting it to a monitor is a real PITA and I am just hoping someone comes by with a "Dude I know what causes that!!!"

Thanks

JTS

Edit: San Dimas High School football RULES!!!  << bonus points if that rings a bell.

---

### Post by FluffyElmo on 2009-02-03
I don't know exactly what it is but I'd start by disabling any onboard devices you don't need. The one time I had an IRQ conflict it was onboard audio. Without attaching a monitor you may still be able to do some debugging...

*dmesg* is usually helpful and logs of previous boots are stored in */var/log/dmesg.x* it's probably worth going through them to see what the exact error is. 

*cat /proc/interrupts* will list the devices that use IRQs, you won't see the conflict once booted but it may give you a start.

---

### Post by jimmy the saint on 2009-02-04
Thanks for the tip.  I just went through the dmesg log (I assume that .1.gz would be the last session?) but it may as well be written in Aramaic.  I didn't see any errors, but unless they would be labeled as such, that doesn't mean there aren't any.  I will tinker with it and disable a few devices.  I only shut it down a few times a year, but I like my stuff to work! 

I'll consider it an opportunity to have a learning experience when I have time for one!

Thanks again

---

