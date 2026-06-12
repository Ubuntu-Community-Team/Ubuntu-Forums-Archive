---
title: "Brightness problem in Ubuntu 11.04"
date: 2011-07-13
forum: Desktop Environments
---

### Post by xdeathcorex on 2011-07-13
I just reinstalled Ubuntu 11.04 on my laptop since there are problems on my phpmyadmin.

Now another problem arise. I can't even see a thing on my monitor screen but the first time I got logged in it was okay, but a little bit dim. So I decide to fix it later.

The second time I logged in after grub menu, it all went black. I did see something appear but it was too dark. I tried to use fn key to change the brightness but none did it.

Thankfully, I dual-booted with Windows 7 and got a chance to Google. Well, I've found some solutions, but how do I apply it since the screen in Ubuntu is so dark, I can't see a thing, seriously.

I did even tried in recovery environment (second in the grub list), but it's still the same.

So, how do I enter my Ubuntu and apply the command?

Here's the command line I've found while Googling.

```
$sudo nano /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="quite splash acpi_osi=Linux”
 GRUB_CMDLINE_LINUX=”acpi_backlight=acer”
$sudo update-grub

```I'm using Acer 4736.


Here's my graphic card infos.
Mobile Intel(R) 4 Series Express Chipset Family


Pls help. Thanks.

---

