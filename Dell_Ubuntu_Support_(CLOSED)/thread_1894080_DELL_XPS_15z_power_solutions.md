---
title: "DELL XPS 15z power solutions"
date: 2011-12-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by feri_crosby on 2011-12-11
hello, finally is Ubuntu working on mz DELL XPS15z but battery life is about 1,5 hour and in windows it used to be about 4 hours....laptop is littbe bit hot than in windows mode, its more noisy, .... and there is no icon to show my battery status...can you help me please?

---

### Post by mikewhatever on 2011-12-11
Can you post the hardware specs, as well as the version of *buntu in use.

---

### Post by feri_crosby on 2011-12-11
Ubuntu 11.10 and hardware: 8GB of memory, 2GB of graphic memory nVidia+optimus, 2.7 ghz CPU.....laptop model number is XPS XPS 15z (L511z)...i have already turned off nVidia graphic card but fans are still noisy + i cant see battery info bar in the top....

---

### Post by berthold_dk on 2011-12-17
> **feri_crosby said:**
> Ubuntu 11.10 and hardware: 8GB of memory, 2GB of graphic memory nVidia+optimus, 2.7 ghz CPU.....laptop model number is XPS XPS 15z (L511z)...i have already turned off nVidia graphic card but fans are still noisy + i cant see battery info bar in the top....

I'm experiencing the same problem, also on Ubuntu 11.10. Here are full specs

Model: XPS 15z 
8192 MB Dual Channel DDR3 SDRAM på 1333 MHz [2 x 4096]
 2048MB NVIDIA® GeForce® GT 525M Grafikkort med Optimus
256 GB Solid State-harddisk
8X dvd+/-rw-drev
Wireless: Intel® Centrino® Advanced-N 6230 (2x2 a/g/n+ Bluetooth Combo Card)
Processor: Intel® Core™ i7-2640M processor 2,80 GHz 
LCD: 40 cm(15,6") WLED-skærm med Full HD (1920 x 1080) og TrueLife™ med 2.0 Mega Pixel Integreret kamera

---

### Post by feri_crosby on 2011-12-18
finally, problem with battery status bar is solved, but battery life is still about one hour. This is killing me! If you wanna know, how to show your battery status in Ubuntu 11.10, download Ubuntu 11.04, install it (remove your Ubuntu 11.10) when running Ubuntu 11.04 it will ask for updates (as default), if not, check your settings and find Update manager. In your update manager is will be an option to UPGRADE your system to Ubuntu 11.10. Run upgrade. Than just follow steps, restart and dont forget edit your grub when booting, ...

---

### Post by berthold_dk on 2012-02-01
The main problem regarding the power consumption seems to be the missing support for the Nvidia Optimus graphics card.

The Bumblebee project is aiming at solving this. It works by disabling the graphics card in a safe way. You can activate the card for specific programs by typing "optirun <program name>" in the terminal.

They just released a 3.0 version, they claim it to be "stable enough for release". 

I followed the installation instructions here [http://askubuntu.com/questions/36930/how-well-do-laptops-with-nvidia-optimus-work](http://askubuntu.com/questions/36930/how-well-do-laptops-with-nvidia-optimus-work) and so far things are working out ok.

I have some 45 extra minutes on battery (2,5 hours in total) and the fan noise also seems to be declining.

---

