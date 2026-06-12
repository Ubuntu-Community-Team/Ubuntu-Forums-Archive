---
title: "Graphics Card affecting desktop enviornment"
date: 2008-03-22
forum: Desktop Environments
---

### Post by mattrobinson999 on 2008-03-22
Ive just installed Ubuntu on my old computer and it was working perfectly until I enabled my correct driver for my graphics card (ATI Radeon 7600)
Now when ever, I reboot I get a message saying...
"Ubuntu is running in low graphics" (800x600)
I click onto the configure option and Ubuntu knows what graphics card I got but uses a "plug and play" monitor where I can only use 800x600 and also uses the "vese - Generic VESA-compliant videocards" instead of my real "ATI Radeon 7600"
Ive enabled the correct graphics drivers in Administration but Ubuntu still wont let me use my preferred 1280x1024.

Does anyone have any advice?

---

### Post by banewman on 2008-03-22
Try 
sudo dpkg-reconfigure xserver-xorg 
in a terminal. Choose the defaults except for the vid card and resolution.
Choose you're installed ati driver and you use the up/down arrows to move to a resolution in the appropriate window and the space bar to select.
:)

---

### Post by trippinnik on 2008-03-22
What do you mean the correct driver for your card?  Were you using the ati opensource driver?  
Anyway, you should be able to configure your monitor manually. Go to System - Administration - Display - Hardware then configure the Monitor. Choose generic with the correct resolution to match your display.

---

