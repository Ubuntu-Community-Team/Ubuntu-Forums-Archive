---
title: "&quot;No kernel modules were found&quot;"
date: 2007-03-18
forum: Development CD/DVD Image Testing
---

### Post by Eluzion on 2007-03-18
Usually I can find a solution to every Ubuntu related problem on these forums but I seem to be stuck with this one. I'm trying to install the latest Herd 5 using the alternate CD (I'm running the GeForce 8800GTS so I have to use the alternate method), but I get an error during install that states "No kernel modules were found...". I've tried two different builds (downloaded from the daily builds) and still the same problem. 

Any ideas?

---

### Post by Syke on 2007-03-18
I was able to just ignore the error and continue with the install. Did you try to continue?

---

### Post by Eluzion on 2007-03-18
I did, but after I reboot (after the installation)... I see my motherboard splash screen and it starts loading Ubuntu but I lose video. I let it side for about 10 minutes and the HDD looked like it was idling and still no image from the screen.

---

### Post by Eluzion on 2007-03-18
Any ideas?

GRUB loads, and it appears to be loading the GUI but then the screen just goes blank and there is no signal. I've tried Ctrl-Alt-Backspace, but nothing. I tried reconfiguring the xorg file or whatever to a lower resolution, but still the same issue. I'm running the GeForce 8800GTS, which I know I will need to install the video drivers manually but shouldn't it at least give me the xserver can't start error message and throw me into the terminal?

Also, there are no network drivers for my motherboard (Intel BX2, 975 chipset). I tried downloading the latest Nvidia drivers through the recovery mode but obviously can't do that either with no internet.

---

### Post by Henrik on 2007-03-19
Hm, odd. I got this same error with the server install, which is like alternate, but my alternate installs were fine.

Apparently it's an ABI incompatability between the kernel and the d-i installer.

**Update:** I've added some bug-category questions to the [**FAQ**]("https://wiki.ubuntu.com/Testing/Community/FAQ").

---

