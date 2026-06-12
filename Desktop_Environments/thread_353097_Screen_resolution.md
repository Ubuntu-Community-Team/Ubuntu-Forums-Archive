---
title: "Screen resolution"
date: 2007-02-04
forum: Desktop Environments
---

### Post by Alie on 2007-02-04
i cant changes my screen resolution to 1280x800.

my vga card info:
Accelerator in Use:		Mobile Intel(R) 945GM Express Chipset Family
Video BIOS:		1313
Current Graphics Mode:	1280 by 800 True Color (60 Hz)

i dont know how to add screen resolution in ubuntu(linux) :(

i'm newbie, so please help me how to add new screen res step by step in my config.

---

### Post by dcstar on 2007-02-04
> **Alie said:**
> i cant changes my screen resolution to 1280x800.

my vga card info:
Accelerator in Use:		Mobile Intel(R) 945GM Express Chipset Family
Video BIOS:		1313
Current Graphics Mode:	1280 by 800 True Color (60 Hz)

i dont know how to add screen resolution in ubuntu(linux) :(

i'm newbie, so please help me how to add new screen res step by step in my config.

Assuming System-Preferences-Screen Resolution won't let you do it, in a terminal:
```
sudo dpkg-reconfigure xserver-xorg
``` will allow you to redetect your hardware and allow the system to use the resolution you set (use the defaults offered, and select the "Simple" option when you get to the Resolution section).

---

### Post by InsomniakF on 2007-02-05
> **dcstar said:**
> 
```
sudo dpkg-reconfigure xserver-xorg
``` 
Worked for me!

I had tried 915resolution and a couple other things and nothing else worked.
Thank you muchly!

---

