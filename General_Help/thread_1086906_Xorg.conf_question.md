---
title: "Xorg.conf question"
date: 2009-03-04
forum: General Help
---

### Post by musket85 on 2009-03-04
I've bought a tv to hook up to my laptop.
The resolutions I'm presented with only go to 1360x768, but the resolutions of my screen is 1366x768, basically theres a black line down one edge thats pissing me off
I've tried editing the xorg.conf file to add the needed resolution under the Screen section, but the custom modeline I need to add to the monitor section has me foxed. I've researched this and the command 

gtf horizontalresolution verticalresolution refreshrate

should give me the modeline I need to enter, however it returns this
 # 0x0 @ 0.00 Hz (GTF) hsync: nan kHz; pclk: nan MHz
  Modeline "0x0_0.00"  nan  0 -2147483648 -2147483648 -2147483648  0 1 4 1  -HSync +Vsync

Anyone offer any help?

---

### Post by emarkay on 2009-03-04
What type of graphics card you have? THE first biggie question!

---

### Post by C-- on 2009-03-04
Could you post your xorg.conf file for us?

---

