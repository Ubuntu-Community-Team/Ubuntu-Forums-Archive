---
title: "HELP, windows boot loader?"
date: 2009-01-04
forum: General Help
---

### Post by nintendo9freak on 2009-01-04
Well i had ubuntu on my laptop as a dual boot with windows vista. So for some reason i couldnt get the driver for my wireless card to work so the internet didn't work so i decided to get rid of ubuntu for now. So i uninstalled it and reformatted the partition ubuntu was on. Now i keep getting the GRUB 17 error and my friend said it because i still have the GRUB boot loader and i need to get the windows boot loader or something but i'm lost can anybody help me please?

---

### Post by the_squircle on 2009-01-04
Basically, you need to replace GRUB with the Windows bootloader. If you have a Windows CD, it's really easy. All you have to do is boot to the Vista disc, but when it says "Click here to install", click the small link at the bottom left to "Repair my computer". Go to the command prompt, and type "C:" (without the quotes) and press enter. Next, type "BOOTREC /FIXMBR" (without the quotes) and press enter. Finally, type "BOOTREC /FIXBOOT" (without the quotes) and press enter. This should replace the Windows bootloader for you, and GRUB will be gone.

Sorry to see you go! If you ever get frusterated with Windows, feel free to come back :)

---

### Post by nintendo9freak on 2009-01-04
wow thanks a lot, it worked, life saver. haha i'll probably try ubuntu again in about a year or so for my cs classes.

---

