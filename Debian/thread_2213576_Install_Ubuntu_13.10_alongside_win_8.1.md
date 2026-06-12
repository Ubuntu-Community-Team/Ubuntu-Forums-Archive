---
title: "Install Ubuntu 13.10 alongside win 8.1"
date: 2014-03-27
forum: Debian
---

### Post by jimmyh1972 on 2014-03-27
Hello

I bought a new computer - asus t100 (atom cpu) it is pre-installed with Win8.1
i want to install Ubuntu alongside win8.1 - I tried with all wubi options (12.04 - 13.10)
and after installation Ubuntu doesnt boot. the error on the screen is - [FONT=Ubuntu Mono]Windows failed to start. A recent hardware or software change might be the cause. To Fix the problem:[/FONT]
 1. Insert your Windows installation disc and restart your computer.
 2. Choose your language settings, and the click "Next."
 3. Click "Repair your computer."

If you do not have this disc, contact your system administrator or manufacturer for assistance.

File: \ubuntu\winboot\wubildr.mbr
Status: 0xc0000098
Info: The selected entry could not be loaded because the application is missing or corrupt.

i tried also disable all uefi & secure boot option - still doesnt boot.

for the moment only the system boot option works - if i choose Ubuntu its not booting.

anyone knows how to solve it?

thank's ahead Jimmi

---

### Post by Bucky Ball on 2014-03-27
*Thread moved to **Other OS/Distro Support**.*

The tip is, and sorry to say, avoid Wubi. It has been abandoned and shouldn't be there as an option as development has stopped and it is no longer officially supported. There are very few people here with much knowledge of it as it is not used much. 

I moved the thread here as your issue appears to be about how to boot Windows. Good luck. ;)

---

