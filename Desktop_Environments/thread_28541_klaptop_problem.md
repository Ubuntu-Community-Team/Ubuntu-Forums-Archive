---
title: "klaptop problem"
date: 2005-04-20
forum: Desktop Environments
---

### Post by diwakergupta on 2005-04-20
I'm not sure if this is an issue with klaptop or ACPI. For those who don't know, klaptop is the little battery monitor applet in the system tray. Here's the problem -- I have configured klaptop to logout and shutdown my laptop when only 5 min of battery life is left. Now, suppose the laptop was PLUGGED IN when I put it to sleep/hibernate mode. 

When resuming, if the laptop is plugged in, there's no problem. However, if the laptop is NOT plugged in while resuming, klaptop immediately thinks 0 battery life is left (even know the battery monitori in gkrellm [which reads values from the acpi proc files] shows that batter IS left) and thus logs me out and shuts the system down.

This is clearly not desirable, because usually when suspending my laptop IS plugged in, and while resuming its usually not plugged in (because I'm in a class or talk or something). Is anyone else seeing this problem?

---

