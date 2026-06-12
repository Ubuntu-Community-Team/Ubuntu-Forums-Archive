---
title: "Custom appearance problem"
date: 2008-03-30
forum: Desktop Effects &amp; Customization
---

### Post by musket85 on 2008-03-30
I'm unable to change to custom from none under appearance.
My graphics card is
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)
I've got compiz installed but not compiz fusion, and I'm not even sure if compiz works without custom effects installed.

---

### Post by aroch1 on 2008-03-30
Try running ```
compiz
``` in a terminal and posting the output so I can get a better idea of the problem.

---

### Post by musket85 on 2008-03-30
This is what I get
compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0176 (rev a3) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity

---

### Post by aroch1 on 2008-04-01
Hmmm, sorry, not the type of compiz error I'm familiar with.

---

### Post by noirtier_de_villefort on 2008-04-01
i believe your problem is in memory allocation... in the BIOS setup, there is an option dealing with how much memory goes to video "stuff".. it needs to be increased... just a minute... i'll post what the exact option is.

---

### Post by noirtier_de_villefort on 2008-04-01
okay... if this is your problem, you need to restart your comp., go into the BIOS, go to "Advanced Chipset Features", then change the "Frame Buffer Size" to 64mb. if that's your problem. it said in your output "Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity" 65536kb is 64mb... that's why i think that's the problem, plus i had to change that value myself.

---

