---
title: "Mode Not Supported Error for Samsung LE40M8"
date: 2008-09-29
forum: Desktop Environments
---

### Post by RoboJ1M on 2008-09-29
Hi,

I have an old Acer Aspire 1300 laptop with an S3 ProSavage KN133 graphics controller. I'm using Xubuntu 8.04 with the savage driver.

It has an external monitor connection, but appears to only be able to drive either the laptop screen or the external screen, not both.

The only way to switch between the two is boot the laptop with the external monitor connected or not connected.

I'm trying to use my Samsung LE40M8 TV as an external monitor. I think it's one of those monitors that lies about it's capabilities.

When X starts, it just displays Mode Not Supported.

So, it looks like I'm going to have to revert to hacking the xorg.conf file. Not really an expert there.

Luckily, the manual for the TV has detailed info about what modes are supported. Here is an example:

Res: 1920x1080 
Horiz: 66.587 KHz
Vert: 59.934 Hz
Pixel Clock: 138.5 MHz
Polarity (h/v) +/-

But I have no idea how to:

1) Turn that into a modeline
2) Setup xorg to only use that modeline when I've got the Samsung connected and to just do what it's doing now when I'm using the laptop screen.

TIA,

J1M.

---

