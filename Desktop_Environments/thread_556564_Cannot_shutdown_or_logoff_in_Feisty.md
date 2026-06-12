---
title: "Cannot shutdown or logoff in Feisty"
date: 2007-09-21
forum: Desktop Environments
---

### Post by skarp7c1 on 2007-09-21
Hello

This is my situation: I've just built a new pc, with a 8800GTS 640mb. I couldn't run the Feisty (64bit) live cd without changing the (F4) vga option to my monitor's native resolution (of 1920x1200) and changing the boot option with out 'quiet splash' and selecting to boot in safe graphics mode. With any other options it would not start.

I was able to install Feisty, but couldn't restart, I shutdown manually. When I powered up, it showed grub loading and after waiting 3 seconds, it was a black screen. I powered down and started up the live cd again. From searching google, I modified the menu.lst , removed 'quiet splash' from the kernel, tried to update grub but couldn't do it from the cd. Failed to reboot again. I was able to log on, done the updates, and tried to install the nvidia drivers, but I must have done something wrong as I got a black screen, and nothing worked.  booted the kernel in recovery. Finally I gave up and decided to reinstall feisty.

I got similar problems, but I was able to restart from the live cd this time. I haven't downloaded any updates or drivers. Modified menu.lst the same way, and tried updating grub, after that the menu.lst reverted to the original version. So I removed 'quiet splash' from #defoptions and after the kernel. Updated grub. Failed to shutdown. 

I can start up the computer and log in just fine. 

When I try to log off/shutdown/restart I only get a black screen, no messages visible, cannot use the keyboard even when it is still on. The only option is to power down manually.

UPDATE: By reading some other threads, I was able to shutdown from terminal using 'sudo shutdown now -hP'.

Could anyone give me any instruction of what I should do to possibly fix this problem. I will probably need help with installing the nvidia drivers, but I'd like to first be able to restart/shut down properly.
Any help will be greatly appreciated.

Thank You

---

### Post by skarp7c1 on 2007-09-21
I managed to install envy, and thanks to it install the nvidia drivers.

Right now it appears I can use my computer normally, log out restart and shutdown work.

---

