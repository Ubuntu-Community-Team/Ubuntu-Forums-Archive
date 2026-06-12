---
title: "[SOLVED] Changing usplash screen using SUM"
date: 2008-05-18
forum: Desktop Environments
---

### Post by alciono on 2008-05-18
Today I installed StartUp-Manager (SUM), and attempted to change the splash screen.

I downloaded and extracted usplash-theme-ugrooth_0_2.so from gnome-look.org then used SUM to set it up. When I rebooted I got the black screen and the error message "Could not start GUI due to some internal error...". I was able to boot in recovery mode, change the link for usplash-artwork.so back to usplash-theme-ubuntu.so, reconfigure the kernel, and then do a normal reboot. I used the following steps to recover, in case someone else encounters this same problem:

1. In recovery mode opened root terminal
2. ln -sf /usr/lib/usplash/usplash-theme-ubuntu.so /etc/alternatives/usplash-artwork.so
3. dpkg-reconfigure linux-image-`uname -r`
4. shutdown 0
5. boot in normal mode once again

Any ideas why this was unsuccessful?

---

### Post by garyedwardjohnston on 2008-05-18
Simply unpack the file then install it.  What is this SUM bit???

---

### Post by alciono on 2008-05-18
I used the StartUp-Manager, which is a GUI utility to change my splash theme. It did not work. How would you install it?

---

### Post by alciono on 2008-05-19
This morning after playing with the StartUp-Manager and restarting I was able to see the splash screen for the first time. So I am marking this thread as solved.

---

