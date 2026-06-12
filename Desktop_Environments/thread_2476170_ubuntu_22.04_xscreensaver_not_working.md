---
title: "ubuntu 22.04 xscreensaver not working"
date: 2022-06-18
forum: Desktop Environments
---

### Post by fire-fly2 on 2022-06-18
Hi
On ubuntu 22.04 the xscreensaver was unable to lock the screen.
I executed "xscreensaver-command -lock", it returned "xscreensaver-command: locking not enabled."
However, the  ~/.xscreensaver indicate lock was enabled.
grep -w lock ~/.xscreensaver
lock:        True

I started Xscreensaver manually, it returned the following message
xscreensaver: 21:49:08: locking is disabled (Cannot lock securely under Wayland)

Please help
Thanks

---

### Post by Dennis N on 2022-06-18
Xscreensaver cannot blank the screen when you use Wayland. You will have to choose Xorg as your session at the login screen (use gear menu, lower right corner of screen)

---

### Post by fire-fly2 on 2022-06-18
Hi 
Thanks.
There was no Wayland login.
In the original/etc/gdm3/custom.conf, Wayland was set to false.
I change it WaylandEnable=true, and execute 'systemclt restart gdm3.
There was no wayland login.
Please see [IMG]https://ibb.co/ySz1mb5[/IMG] 
([see https://ibb.co/ySz1mb5]("https://ibb.co/ySz1mb5"))

---

### Post by #&amp;thj^% on 2022-06-18
This annoyance was around in 20.04 as well:
```
gsettings get org.gnome.desktop.lockdown disable-lock-screen
```
most of the complaints came from users using multiple DM's lightdm GDM3.
Check if this works:
```
dm-tool lock
```
and also double check in settings if: Settings > Privacy > Screen Lock has all your desired settings. You may have to toggle on or off deactivating Lock Screen

---

### Post by Dennis N on 2022-06-18
> **fire-fly2 said:**
> 
There was no wayland login.

The password box must be open, then the session selection icon will appear. See screenshot.

---

