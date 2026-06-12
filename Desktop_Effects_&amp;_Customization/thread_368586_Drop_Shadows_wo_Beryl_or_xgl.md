---
title: "Drop Shadows w/o Beryl? or xgl?"
date: 2007-02-23
forum: Desktop Effects &amp; Customization
---

### Post by xanimal on 2007-02-23
I have an older Dell Inspiron 4000 Laptop (PIII 800, 512MB RAM) running Mint Linux 2.2 that has been my workstation for quite some time. It has the ATI Rage Mobility 8MB (rev 02) video in it. As far as I know, it is not able to do the 3D rendering that Beryl and others do. I am ok with that, but is there a way to add drop shadows and possibly some transparency to the Gnome environment? 

For example, I also dual boot to XP and have drop shadows via Yz Shadows, and it runs that beautifully. Any ideas?

---

### Post by shrndegruv on 2007-02-23
In order to get drop shadows you would need to use the radeon drivers, enable the composite extension in your xorg.com, and use xcompmgr to get the desired effect.  I dont know if your hardware can handle it though.

You might want to look into e17, which is very pretty but built to run on minimal hardware.   e17 also does drop shadows with no outside dependencies, however they only exist within one canvas (or layer, im not sure of the terminology).  This means that a window that sits over the background will throw a shadow on the background, but if you move that window over another window, there will be no shadow over the other window.

---

### Post by xanimal on 2007-02-23
I've played with E17 but it just wasnt for me. Odd that someone hasnt written something like Yz Shadow for linux.

---

### Post by Ptero-4 on 2007-05-11
xanimal. xcompmgr is the Yz Shadow equivalent on linux.

---

