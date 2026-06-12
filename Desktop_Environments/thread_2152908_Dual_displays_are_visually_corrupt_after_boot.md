---
title: "Dual displays are visually corrupt after boot"
date: 2013-06-09
forum: Desktop Environments
---

### Post by rebelxt on 2013-06-09
I have installed Kubuntu 13.04 on a system with this hardware:

    ASUS P8Z77-M Pro mother-board
    i5-3550 CPU with integrated HD Graphics 2500 (Intel Corporation Ivy Bridge Graphics Controller (rev 09))
    16GB RAM
    1600x1200 DVI monitor
    1920x1080 HDMI monitor

The system boots correctly through the login, after which I see this (photograph):
[ATTACH=CONFIG]243685[/ATTACH]
A strip from the right side of the HDMI display is showing on the left side of the screen.

A screenshot, giving no indication of any problem, shows what should be visible:
[ATTACH=CONFIG]243684[/ATTACH]

Then I launch "System Settings" > "Display and Monitor", disable the HDMI monitor, click the Apply button, and wait a few seconds for the system to reset the display. Then I enable the HDMI monitor, again click the Apply button and wait for the display to be reset. At this time everything works fine ----- until the next boot, or logoff/logon, when I have to repeat the procedure.

When I first built this computer, I installed Linux Mint 13 which would not work until I installed a 3.4.? series linux kernel. Remembering that, I installed a 3.4.6 kernel in Kubuntu 13.04. When booting from that kernel, there is no problem with the display.

FYI, I see the same problem with Linux Mint 15. However, the problem does not show in a virtual machine or when using the live disk.

1. Is this a known problem or is it just me?
2. Does a bug need to be reported? If so, where?
3. Can I expect any difficulties using the older kernel?

If it helps, here are links to the Xorg logs after booting each kernel:
[https://www.dropbox.com/s/9wz0q5azzc2x61k/kernel_3.4.6_Xorg.0.log]("https://www.dropbox.com/s/9wz0q5azzc2x61k/kernel_3.4.6_Xorg.0.log")
[https://www.dropbox.com/s/14n8ia38lpr1fvl/kernel_3.8.0_Xorg.0.log]("https://www.dropbox.com/s/14n8ia38lpr1fvl/kernel_3.8.0_Xorg.0.log")

---

### Post by rebelxt on 2013-06-10
bump

---

