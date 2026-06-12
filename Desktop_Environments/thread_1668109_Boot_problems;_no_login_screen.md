---
title: "Boot problems; no login screen"
date: 2011-01-15
forum: Desktop Environments
---

### Post by iknowcss on 2011-01-15
A few minutes ago, I rebooted my Ubuntu 10.10 (64-bit) box to see if a few changes to /etc/fstab stuck. Once it finished rebooting, I couldn't get to the login screen. The startup looked normal, and the last thing I see before a black screen is the low-res "Ubuntu 10.10" splash with the dots underneath. The monitor does not go into power save mode. I went into recovery mode and #commented out the changes I made and rebooted, but that didn't change anything. In failsafe text-only mode, I ran this command thinking maybe there was a problem with my X server.
```
sudo dpkg-reconfigure xserver-xorg
```
So far, I've made no progress. I don't know what error logs I should be looking at, either. Anyone have an idea what the problem might be? Thanks in advance

---

### Post by iknowcss on 2011-01-15
Figured out a fix. I don't know why, but my /etc/X11/xorg.conf seems to have been corrupted. I was able to fix the problem by booting into recovery mode (hold shift while booting). I used a network enabled terminal to run the command
```
cp xorg.conf xorg.conf-broken
cp xorg.conf.failsafe xorg.conf
```
Once I had my regular startup working with failsafe graphics, I ran the installation script for my video card drivers and all is working fine again

---

