---
title: "NVidea Nouveau driver freeze"
date: 2017-07-22
forum: Desktop Environments
---

### Post by joseraeiro on 2017-07-22
Greetings,

I am using Lubuntu 17.04 for some time now.

I was using NVidea's proprietary driver until now but I decided to give the Nouveau driver a chance.

After applying the Noveau driver I rebooted but the resolution was very low. Henceforth, I did "apt get install xserver-xorg-video-noveau". It installed all necessary packages.

* Then I rebooted and, at the time that the login screen should appear, the screen stays blank, with the cursor on the top left of the screen appearing and disappearing. *

I've tried hitting the Shift key to get the GRUB menu but it doesn't show up. I've tried pressing Shift + Alt + F1 (or 1) to try and get to the command line but no luck.

I'm able to access the HD using a Live CD.

What can I do to revert the NVidia driver settings to the configuration that worked?

Thanks in advance!

---

### Post by joseraeiro on 2017-07-22
I was able to remove the nouveau driver and install the package nvidia-current. I've also performed nvidia-xconfig ont the terminal to create the xconf.org file. 

Now the NVIDIA logo appears and after that the login window. Alas, when the login window appears everything is frozen: the keyboard, mouse, etc. I'm unable to get to a terminal by alt ctrl F1.

---

