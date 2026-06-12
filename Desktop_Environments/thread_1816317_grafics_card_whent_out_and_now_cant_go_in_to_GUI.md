---
title: "grafics card whent out and now cant go in to GUI"
date: 2011-08-01
forum: Desktop Environments
---

### Post by jwflammer on 2011-08-01
Hey my GF tripped over a cable which broke my graphics card. I have on board graphics that work fine, but now it wont boot into x server. Just the terminal login screen. what do i do in terminal to fix this? so i can go back to just using on board graphics.

---

### Post by coffeecat on 2011-08-01
What is the broken graphics card? What is the onboard graphics? Did you install a proprietary video driver for the broken card?

If you install the proprietary driver for a nvidia card and try to boot up with an ATI GPU, the xserver will fail, and ditto for ATI proprietary driver and nvidia GPU. If you are in this situation, you need to uninstall the proprietary driver and remove /etc/X11/xorg.conf from the CLI. Then the system will load the appropriate open source driver for your onboard card when you boot up.

If you need help with that, post back.

---

### Post by jwflammer on 2011-08-01
Yeah there both nvidia graphics cards but for some reason i cant boot into x server ill try and remove the xconfig file and reboot

---

### Post by coffeecat on 2011-08-01
Yes, but which nvidia cards and did you install the proprietary driver? If so, did you install it from Additional Drivers or downloaded from the nvidia site? Different nvidia GPUs may need different versions of the driver.

---

### Post by jwflammer on 2011-08-01
i let ubuntu do all the work all i had to do was go into hardware drivers and activate the divers

---

### Post by jwflammer on 2011-08-01
the onboard is a 6100 gforce and the card is a 5600 gforce its not working i have remove the xorg.conf files and still it boots up and goes dirctly into terminal log on screen and when i alt F7 to the desktop it just sits there with a unscore blinking

---

### Post by xdominex on 2011-08-01
Did you try typing "sudo gdm" and/or "startx" in terminal?

---

