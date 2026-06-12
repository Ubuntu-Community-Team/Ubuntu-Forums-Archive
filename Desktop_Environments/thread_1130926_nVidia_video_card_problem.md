---
title: "nVidia video card problem"
date: 2009-04-20
forum: Desktop Environments
---

### Post by stargazer418 on 2009-04-20
I recently installed Ubuntu 8.10 on the second hard drive on my computer. The first has Windows XP. When I started Ubuntu the first time, I was stuck in 800x600 resolution, and it automatically recognized my Linksys USB wireless adapter. I used my wireless connection to go to nVidia's website and downloaded the Linux x86 driver for my GeForce4 MX video card. I installed it by booting into the "recovery mode" as it was the only option that got me to a command prompt with no X environment. I installed it by typing:```
sudo sh NVIDIA-Linux-x86-96.43.11-pkg1.run
``` and followed the directions. It installed successfully, so I rebooted into Gnome. It showed the nVidia logo before it went to the desktop, and the desktop was at my monitor's native resolution of 1024x768, but my network connection was gone and for some reason there were no window borders or decorations. If I opened Firefox, it would say "The page cannot be displayed" and at the top of the screen, instead of being the usual orange title bar, it stopped at the menu bar. :confused: Please help!

EDIT: I know why it wouldn't see the network! I clicked "Deny" when it asked for my Keyring password! The network works fine now, but still no window borders.

---

### Post by cariboo on 2009-04-20
Did you try System-->Administration-->Hardware Drivers? To install the restricted video drivers, and there might be drivers for your wireless card may be there too.

Jim

---

### Post by stargazer418 on 2009-04-20
It comes back saying "No proprietary drivers are in use on this system" and a blank list.

---

### Post by stargazer418 on 2009-04-20
Another thing that I forgot to mention: I used to have 8.04 (Hardy) on the same computer, but I uninstalled it. The first time I started up Hardy, it showed the Hardware Driver icon in the notification area and I was able to install the restricted driver. I then used Ndiswrapper to install the wireless drivers. Why didn't it pop up the option to install the restricted drivers in Intrepid like it did in Hardy?

---

### Post by andrea000 on 2009-04-20
Have you tried [envyng]("http://albertomilone.com/envyngfaq.html") it's in the repo's may help install the correct driver for your graphic card if you have a nvidia or ati card

---

### Post by stargazer418 on 2009-04-20
> **andrea000 said:**
> Have you tried [envyng]("http://albertomilone.com/envyngfaq.html") it's in the repo's may help install the correct driver for your graphic card if you have a nvidia or ati card
Thank you andrea000! EnvyNG worked like a charm and now I have desktop effects enabled and I still have my title bar!

---

### Post by andrea000 on 2009-04-20
Your welcome always happy to helped out.

---

