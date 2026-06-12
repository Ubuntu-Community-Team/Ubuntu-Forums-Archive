---
title: "Xubuntu offen offen crash"
date: 2006-07-06
forum: Desktop Environments
---

### Post by PENG on 2006-07-06
I had install Xubuntu 6.06 on my old laptop. 
When running firefox, computer will suddenly halt, and I can input any key,
or click any icon. What I can only do is to reboot computer. This case does not occur once I start firefox, but if I run firefox some time, crash will surly come.
I have no idea to deal with this problem, and consult experts here for help.
Thanks.

---

### Post by dolby on 2006-07-06
4) If you have an AGP graphic card and your system freezes but you can still move the mouse pointer you will have to do this:

```
sudo nano /etc/X11/xorg.conf
```


Add the lines which begin with the word "Option" in this section of the file:

```
Section "Device" 
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]" 
Driver "nvidia" 
BusID "PCI:1:0:0" 
Option "NvAGP" "0" 
Option "RenderAccel" "Off" 
Option "IgnoreDisplayDevices" "DFP,TV" 
Option "NoRenderExtension" "Off" 
Option "AllowGLXWithComposite" "Off" 
EndSection
```


Then save the file and exit. Press CTRL+ALT+Backspace in order to restart the xserver.

IF it doesn't work yet then you can add also the following line which will disable 3d acceleration

```
Option "Accel" "Off"
```


If this doesn't work for you try asking on the Unofficial Nvidia Forum and you might be talking to some of the developers of the NVIDIA drivers (there's a Linux section) (it's very useful) " [http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by PENG on 2006-07-07
> **dolby said:**
> 4) If you have an AGP graphic card and your system freezes but you can still move the mouse pointer you will have to do this:

```
sudo nano /etc/X11/xorg.conf
```


Add the lines which begin with the word "Option" in this section of the file:

```
Section "Device" 
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]" 
Driver "nvidia" 
BusID "PCI:1:0:0" 
Option "NvAGP" "0" 
Option "RenderAccel" "Off" 
Option "IgnoreDisplayDevices" "DFP,TV" 
Option "NoRenderExtension" "Off" 
Option "AllowGLXWithComposite" "Off" 
EndSection
```


Then save the file and exit. Press CTRL+ALT+Backspace in order to restart the xserver.

IF it doesn't work yet then you can add also the following line which will disable 3d acceleration

```
Option "Accel" "Off"
```


If this doesn't work for you try asking on the Unofficial Nvidia Forum and you might be talking to some of the developers of the NVIDIA drivers (there's a Linux section) (it's very useful) " [http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)


Thank your reply. My computer has ATI graphic card, and when computer freezs, I can not do anything, including moving mouse pointer.

---

