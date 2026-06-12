---
title: "XGL help"
date: 2008-02-14
forum: Desktop Effects &amp; Customization
---

### Post by mason215 on 2008-02-14
when ever i try to install this and then reboot it just hangs at the light brown screen and then puts me back at the login screen here's some info

mason@mason-desktop:~$ lshw -C video
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: VT8378 [S3 UniChrome] Integrated Video
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: vga bus_master cap_list
       configuration: latency=32 mingnt=2
mason@mason-desktop:~$ glxinfo | grep -i direct
direct rendering: Yes


thanks

---

### Post by mason215 on 2008-02-14
bump

---

### Post by santiagoward2000 on 2008-02-15
> **mason215 said:**
> when ever i try to install this and then reboot it just hangs at the light brown screen and then puts me back at the login screen here's some info

mason@mason-desktop:~$ lshw -C video
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: VT8378 [S3 UniChrome] Integrated Video
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: vga bus_master cap_list
       configuration: latency=32 mingnt=2
mason@mason-desktop:~$ glxinfo | grep -i direct
direct rendering: Yes


thanks

Hi!
I'm sorry to tell you this, but I think your card isn't supported by XGL. You should remove it if you want to access to your desktop.
Sorry again.

---

