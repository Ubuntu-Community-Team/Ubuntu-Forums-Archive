---
title: "Problem: Dell Studio 14z Loud Popping on Halt in Kubuntu 9.10 i386"
date: 2009-12-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kubuntoid on 2009-12-29
I recently purchased a Dell Studio 14z and installed Kubuntu 9.10 i386 on it. Since the first time I shut down the computer, the speakers have made a loud popping noise along with the screen's backlight flashing brightly right before system halt. I have installed the latest Nvidia drivers available in the proprietary drivers list and the sound works fine while the laptop is on. Can anyone help me fix the popping and flashing on shutdown?

Thanks,
    kubuntoid

Here is the laptop's hardware:
Dell Studio 14z (Studio 1440):
- Intel Core 2 Duo T6600, 2.2GHz, 800Mhz, 2M L2 Cache
- 14.0  HD+ TL LED Display w/Cam (900p screen res)
- NVIDIA MCP79MX (GeForce 9400M G)
- Dell Wireless 1397 802.11g    Half Mini Card (compiled 32-bit broadcom hybrid drivers myself)
- Integrated High Definition    Audio 2.2 (no idea what this is exactly)

---

### Post by dimoftheyard on 2010-01-03
I seem to have the same problem on a Dell Vostro 1720 running Kubuntu 9.10 with the pae kernel. Right before shutdown there is a terribly loud noise. Sound works perfectly while the computer is running, but even when I turn off sound before I shutdown the laptop it beeps very loud. I already blacklisted pcspkr. I, too, am using the proprietary Nvidia driver.
I used Kubuntu 9.04 on the same laptop before and there was no such problem, it appeared after the upgrade.

---

### Post by dimoftheyard on 2010-01-10
I seem to have found a workaround... I turned of the splash screen (edited /etc/default/grub and changed GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="quiet", and ran update-grub, both with sudo), and now after that my laptop didn't beep. So far I tested it only once, but the laptop used to beep every time, and now it didn't.
I don't have a splash screen anymore, but if those beeps go away I'm more than happy with that solution.

---

