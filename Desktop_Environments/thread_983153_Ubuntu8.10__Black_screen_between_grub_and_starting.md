---
title: "Ubuntu8.10 : Black screen between grub and starting of gnome"
date: 2008-11-15
forum: Desktop Environments
---

### Post by bd@cb8be8510 on 2008-11-15
I did a fresh install of Ubuntu8.10. Everything installed right out of the box! :KS I have a minor issue. After selecting Ubuntu8.10 in the grub, my monitor gets dark and gives me a warning "Out of range, Vf : 86.7, HF : 46.4K). The monitor remains in this state until desktop is being loaded.
I encounter the same effect when I shutdown Ubuntu. As soon the system starts to shutdown, the same warning pops up on the monitor. With my former Ubuntu-installs I got the notorious "brown" screen before the desktop was loaded. (My monitor-resolution = 1280 * 1024 (5:4) 75hz). How can I avoid these monitor-warnings? Maybe there are harmful? :?

---

### Post by gwoodruff on 2008-11-15
If you download StartUp-Manager from synaptic you can change the resolution during boot / shutdown. that will get rid of your warning.

---

### Post by bd@cb8be8510 on 2008-11-16
> **gwoodruff said:**
> If you download StartUp-Manager from synaptic you can change the resolution during boot / shutdown. that will get rid of your warning.
It looks to me that this feature is rather a gui for setting up /boot/grub/menu.lst. I set the resolution to 1280 * 1024 for the grub, but I still get a black screen temporarily. 

I found the following message in dmesg :

 [    0.000000] Kernel command line: root=UUID=f112dcc5-3ddc-43d3-85f6-8066ae053928 ro quiet splash vga=775

---

### Post by karlr42 on 2008-11-16
Set it to the lowest resolution (640) rather than the max your monitor can support- remember that at the boot up stage the advanced graphics drivers aren't loaded yet to support all resolutions. For example, my screen has a max res of 1440*900, which I'm using now, but the max I can select in Start-Up Manager is 1024 because the nvidia driver isn't loaded at that stage.

---

### Post by bd@cb8be8510 on 2008-11-16
After setting the resolution to 640*480 and restarting Ubuntu, I get the typical Ubuntu progress-bar back. Problem solved! I appreciate your advice very much!

---

