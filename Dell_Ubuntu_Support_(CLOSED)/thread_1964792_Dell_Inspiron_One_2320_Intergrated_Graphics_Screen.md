---
title: "Dell Inspiron One 2320 Intergrated Graphics Screen Flicker On and Off."
date: 2012-04-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by saratliff on 2012-04-24
Model:

Dell Inspiron One 2320  /  Dual Boot Windows 7 & Ubuntu 12.04 LTS 

Integrated Graphic Card:

Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)


CPU G630 @ 2.7 (two) / VESA: Intel®Sandybridge Desktop Graphics Experience Standard



I can only get the graphics to work in Fail Safe Mode.  When booted up normal, the screen will remain off then randomly blink on and off.

Any help will be greatly appreciated.

---

### Post by drumour on 2012-04-28
I have the previous model 2310, it all works out the box with Ubuntu 11.10. Assuming that the screen is working fine in Win7, you may want to try this just to see if it works / as a temporary solution. It may be irrelevant for you but the 2310 touchscreen is in the process of being patched for 12.04.

---

### Post by vb7ue on 2012-06-17
> **saratliff said:**
> Model:

Dell Inspiron One 2320  /  Dual Boot Windows 7 & Ubuntu 12.04 LTS 

Integrated Graphic Card:

Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)


CPU G630 @ 2.7 (two) / VESA: Intel®Sandybridge Desktop Graphics Experience Standard



I can only get the graphics to work in Fail Safe Mode.  When booted up normal, the screen will remain off then randomly blink on and off.

Any help will be greatly appreciated.

I am having the exact same issue. Were you able to solve this? Please help if you were able to solve the issue! Thanks!

---

### Post by moretime on 2012-06-24
Install 
To install latest release of Grub customizer 2.5.5 in Ubuntu 12.04 and  LinuxMint use the following PPA

sudo apt-add-repository ppa:danielrichter2007/grub-customizer 
sudo apt-get update 
sudo apt-get install grub-customizer

then in preferences add nomodeset to kernel parameters and save changes

then reboot

---

