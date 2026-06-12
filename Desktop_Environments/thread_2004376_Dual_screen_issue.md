---
title: "Dual screen issue"
date: 2012-06-15
forum: Desktop Environments
---

### Post by ivan_californias on 2012-06-15
Hello,

I'm trying to be able to see the Lubuntu desktop in two monitors.

The first monitor is attached to an Intel Poulsbo VGA controller, the other monitor is a USB 7inch LCD DisplayLink Monitor.

The issue it's that when I plug the DisplayLink monitor I see a green screen, then I reboot, and then only it can seen the desktop in this monitor (DisplayLink), and the other monitor turns black. Then when reboot again and unplugged the DisplayLink monitor, the desktop goes back to the main monitor. I can't see the two monitors in the monitor settings.

I have an Dual Core Intel Atom Z530 with Lubuntu 12.04

If some of you have some idea of what's wrong, please let me know.
Thanks in advance.

---

### Post by Gaygerbil on 2012-06-18
You might have to go into monitor settings under preferences and actually turn on the monitor through there. It also depends on your graphics driver, if you have NVIDIA drivers they also have settings for dual monitor displays.

---

### Post by ivan_californias on 2012-06-21
The driver of the monitor is Intel Poulsbo, the other monitor is a USB displayLink Monitor (I think i missed that in the post). The issue is about when I use the usb monitor, the only screen that I can see in the monitor settings is that. I can't see the main monitor.

---

### Post by deadite66 on 2012-06-30
Never managed to get displaylink working properly and i've really tried.
i have gotten displaylink as screen0 and radeon as screen1 but having all the desktop menu's on a 7" screen is useless.

best i can manage is running a seperate X instance for the displaylink screen and using x2x to move the mouse between them but you can't move windows between screens.


it's so easy to use in windows but mostly useless in linux.

---

