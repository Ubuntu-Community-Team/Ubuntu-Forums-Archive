---
title: "X crashed and cannot be restarted: running from a LiveCD right now"
date: 2007-05-11
forum: Desktop Environments
---

### Post by freehunt on 2007-05-11
I kept having stability issues, most of the time during resolution changes from games that don't support 1440X900, and I have never had my system running for more than a day because of it. However, it crashed just now, and when I reboot, X will not start. I run the command startx, and it says the display cannot be configured. Is there a way I can reconfigure it from the LiveCD? I don't want to have to reinstall my system after a hard week of setting things up just right, and I have only been using this for a week, so I am not real used to the CLI.

I am using a Dell E1705 Laptop with 2GB of RAM and the nVidia 7800 Go, running Gnome with Compiz installed. Anything else you need to know, just ask, but I really want to get this fixed without reinstalling. Thanks!

---

### Post by freehunt on 2007-05-11
Alright, so I've tried sudo dpkg-reconfigure xserver-xorg. I've also tried sudo dpkg-reconfigure -phigh xserver-xorg. Neither worked. Is there a way I can reset the xorg.config back to default? Please, I really need this done within a reasonable timeframe, no one has responded here in an hour!

---

### Post by freehunt on 2007-05-11
Well, I got it booted back into X eventually, but there were no borders on the windows for some reason, and things were running very slowly. I decided to just back things up and reinstall, there wasn't much else I knew how to try.

---

