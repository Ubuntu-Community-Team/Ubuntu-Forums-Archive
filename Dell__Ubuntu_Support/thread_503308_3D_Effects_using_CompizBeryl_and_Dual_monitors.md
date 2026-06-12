---
title: "3D Effects using Compiz/Beryl and Dual monitors"
date: 2007-07-17
forum: Dell  Ubuntu Support
---

### Post by tallguy240 on 2007-07-17
Hey Everyone.  After a little work I got my Dell D620 running Feisty and all of my peripherals working as well - USB drives, network multifunction printer/scanner etc. My proudest part of this whole thing is getting it all to work thru my Dell Docking station and Dual 20.1 inch Dell monitors. I would like to try out the 3d effects of Beryl/Compiz as well since I have the Quadro NVS 110M /GeForce Go 7300. Has anyone set this up before in this type of similar config. I just got this thing to look and work the way I like it so if the general consensus is not to muck with it then I will leave it alone. The config is below.

Latitude D-620
Intel Core 2 Duo @ 2Ghz
2Gig RAM 
80 Gig 7200rpm HD
Dell 1490 Wireless - ndiswrapper configured
nVidia Quadro NVS 110M/ GeForce Go 7300 -256MB

System connected to a Dell Latitude/Inspiron D-Port Replicator.
 Modem jack
 Ethernet: 10/100/1000 Mbps
 S-video out
 DVI out
 VGA analog out
 Serial port
 Parallel port
 2 PS/2 connections for keyboard & mouse
 S/PDIF jack
 3 rear USB ports
 1 side USB port
1 side line-out/headphone jack 

This is connected to Dual 20.1 Wide E207WFP LCD monitors with 1 monitor utilizing the vga connection and the other utilizing the DVI connection.


Thanks to all.

---

### Post by dougfractal on 2007-07-17
1.    >system>administration>restricted_drivers_manager >  Nvidia enable
2.   ```
sudo nvidia-settings
```
3.   >X Server Display Configuation > { configure twinview for one desktop on dual screen and SAVE }
4.    ```
 sudo nvidia-xconfig --add-argb-glx-visuals
```


That should be X setup now follow a Beryl or compiz-fusion guide

---

### Post by tallguy240 on 2007-07-23
The DualView part i had running already. Unfortunately the compiz or Beryl stuff did not work. Thats ok though. Im just glad I got dualview working and that when I re-dock it after travelling it remembers the settings.  Thanks for the assistance.

---

