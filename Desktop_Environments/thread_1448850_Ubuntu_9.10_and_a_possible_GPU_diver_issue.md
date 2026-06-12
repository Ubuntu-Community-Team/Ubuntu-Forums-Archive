---
title: "Ubuntu 9.10 and a possible GPU diver issue"
date: 2010-04-07
forum: Desktop Environments
---

### Post by killchain on 2010-04-07
Hello there. I'm relatively new to Linux, I've only used Ubuntu 8.04/8.10 for a while around year and a half ago. Recently, I decided to give Karmic Koala a try on a my current machine running XP Pro by that time - ECS nForce3-A, AMD Sempron 2800+@2GHz, 1GB A-Data DDR400, EPoX Radeon 9550, a primary Seagate Barracuda 7200.10 250GB SATA and an 80Gig Samsung ATA drive on which I made an ext4 partition for Ubuntu. Everthing got up and running in no time (using GRUB 1.97). For several days I played around with the new OS, everything was running fine until a power failure caused my system to stop. On the next start it booted normally, but when the desktop should have come up, I only got a white screen and the cursor. As Compiz was running, I managed to switch to metacity blindly (Super + R, "metacity --replace") and spent a lot of time playing around with the video driver as this seemed to be the problem, but nothing. I tried both the proprietary and the open-source one (although I'm a bit confused which is which). I've read about similar issues with both ATi and nVidia chips, but everything was running fine, I don't see why it fails now. I tried invoking a command screen (Ctrl + Alt + F1) and using dpkg-reconfigure xserver-xorg, but that gave me nothing. Same thing happened when I tried that command in recovery mode - no output, just a new blank line.
So I'll be glad to have my Ubuntu back, any help will be highly appreciated. Thanks for the attention.

[COLOR="Silver"]P.S. I'm not sure if I'm posting in the right section of the forum, move the thread if I'm wrong.[/COLOR]

---

