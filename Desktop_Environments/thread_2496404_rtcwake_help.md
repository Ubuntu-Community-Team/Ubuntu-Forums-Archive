---
title: "rtcwake help"
date: 2024-03-26
forum: Desktop Environments
---

### Post by fence5042 on 2024-03-26
I'm using rtcwake on Ubuntu 22.04 LTS to automate sleeping and waking the computer at certain times. The settings say that the display should turn off after 5 minutes of inactivity, but when the computer wakes automatically with rtcwake, the display never turns off - instead, it just shows a black screen with nothing but the mouse. If I wiggle the  mouse around manually or press a button on the keyboard, the desktop will appear and then 5 minutes later, the display will turn off properly. I looked into ways of automating keyboard/mouse inputs, but this seems very challenging with Wayland. Are there any other workarounds for this?

---

### Post by hyperlinxe on 2024-04-11
Your computer takes a nap, then wakes up, but when it wakes up, it is not fully awake yet! That is an interesting problem.

It sounds like your process needs rethinking. You let the monitor turn off after 5 minutes, then at some point the system goes to sleep,

then at some point, the system wakes up from sleep.  I would try removing the step in your process to turn off the monitor, and let

the system sleep, and then wake up again. 

**[https://man7.org/linux/man-pages/man8/rtcwake.8.html](https://man7.org/linux/man-pages/man8/rtcwake.8.html)**
> 
       Some PC systems can&#8217;t currently exit sleep states such as **mem**
       using only the kernel code accessed by this driver. They need
       help from userspace code to make the framebuffer work again.

       > **-n**, **--dry-run**
           This option does everything apart from actually setting up
           the alarm, suspending the system, or waiting for the alarm.

---

