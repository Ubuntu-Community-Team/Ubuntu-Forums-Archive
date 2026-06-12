---
title: "Keyboard Lock Sometime"
date: 2007-02-18
forum: Desktop Environments
---

### Post by MagiSu on 2007-02-18
Hello, everyone!

I am using KUbuntu 6.10, with KDE 3.5.6. I frequently found when I am using K applications, especially KDevelop and Kate, the keyboard is locked without any reason. I just cannot type anything and can only use mouse. Can you show me a way to solve this?

Thanks a lot!

---

### Post by viper233 on 2007-10-15
Hi MagiSu, 

I'm having the exact same issues, very annoying, unable to pinpoint it so far as there are no kernel messages (dmesg, /var/log/messages, /var/log/Xorg.0.log)  and no X error messages either. The LEDS are also inactive. 
The Mouse is still active. Restarting X via logging out (or ctrl+alt+bksp) makes the keyboard responsive again.

This problem has persistently occurred with ubuntu Edgy

xserver-xorg                               7.1.1ubuntu6.2
nvidia-glx                                 1.0.8776+2.6.17.8-12.3
linux-restricted-modules-2.6.17-12-generic 2.6.17.8-12.3
Linux    2.6.17-12-generic

This problem occurred on the previous hardware that this system was running and now also on it's new hardware. The only original components from the change over are the hard drive and monitor.

---

