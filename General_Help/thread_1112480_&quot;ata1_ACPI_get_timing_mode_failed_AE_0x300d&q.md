---
title: "&quot;ata1: ACPI get timing mode failed AE 0x300d&quot;"
date: 2009-03-31
forum: General Help
---

### Post by xboxmods3077 on 2009-03-31
Hello folks.

    As the post title states, I am seeing this message when I start up my computer. First, I see grub, I select my kernel to boot, and then I see "Starting up". That disappears, and then I see "ata1: ACPI get timing mode failed AE 0x300d". My system continues to boot normally and as far as I know, there are no major problems. I just think that message is annoying as I have never seen it before.

My setup is a Dell Dimension 4100 P3 933mhz
nVidia geforce MX440 32MB Graphics
Running Ubuntu Hardy Heron with all updates to date.
Kernel 2.6.24-23-generic

I have been running ubuntu for awhile so I know my way around it pretty well. I have googled this problem but have only came up with cases where people are experiencing this problem during suspension/resume which is not my case and I couldn't even get an idea here (which is why am in the "General" forum) besides something to do with DMA

Anyone have an idea on how to rectify this?

---

### Post by jdeppel on 2009-05-18
I have this same exact problem...

However, IIRC, it did not appear until after I made the jump to 9.04 from 8.10. I could be wrong though...

---

### Post by jdeppel on 2009-05-19
I'm not sure if you found a solution, but I stumbled across one...maybe it will work for you too.

I changed my settings under System>Preferences>Power Management and set "Put computer to sleep when inactive for:" to "1 Hour." I then rebooted, then changed it back to "Never." The "error" message hasn't appeared since.

---

### Post by Lykopis on 2009-10-10
The ACPI timing error seems to involve some ata drivers, but also has something to do with the way the 80 pin/conductor drive cable is detected. I have a PC that has an 80 pin on the primary and a 40 pin on the secondary. The error only shows on the primary where the 80 pin is, not the secondary where the 40 pin is at. I was able to remove the error by using a add in card, something like an old promise 100/133. It's worth a try if you have one lying around.

---

