---
title: "Can not change back to Generic VESA driver"
date: 2008-03-09
forum: Desktop Environments
---

### Post by Vaftrudner on 2008-03-09
Hello everyone!

A strange problem here. Since I had some problems with 3D, I tried changing my video card driver (I'm using an Intel ICH8 chipset). I went to System -> Administration -> Screens and Graphics. In the tab "Graphics card", the first field had "intel" and the one under it "vesa - Generic VESA-compliant video cards". I went to Choose driver by model and used Intel 945. It automatically chose i810. I rebooted to test it, and now the screen is automatically limited to 640x480. I have tried changing it back to Generic VESA, but when I do that in the same window and press OK, the changes do not seem to take effect. When I go back into the "Screens and Graphics" window, i810 is still used. If I change the setting and reboot, the i810 is still used.

Any suggestions? Thanks in advance!

---

### Post by overdrank on 2008-03-09
> **Vaftrudner said:**
> Hello everyone!

A strange problem here. Since I had some problems with 3D, I tried changing my video card driver (I'm using an Intel ICH8 chipset). I went to System -> Administration -> Screens and Graphics. In the tab "Graphics card", the first field had "intel" and the one under it "vesa - Generic VESA-compliant video cards". I went to Choose driver by model and used Intel 945. It automatically chose i810. I rebooted to test it, and now the screen is automatically limited to 640x480. I have tried changing it back to Generic VESA, but when I do that in the same window and press OK, the changes do not seem to take effect. When I go back into the "Screens and Graphics" window, i810 is still used. If I change the setting and reboot, the i810 is still used.

Any suggestions? Thanks in advance!

HI and have you tried to configure your xorg with this command in the terminal ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Vaftrudner on 2008-03-09
> **overdrank said:**
> HI and have you tried to configure your xorg with this command in the terminal ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
That did it! Thanks mate :)

---

