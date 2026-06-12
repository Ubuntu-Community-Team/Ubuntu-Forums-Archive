---
title: "Problems with X-Server"
date: 2005-12-22
forum: Desktop Environments
---

### Post by DeathOnJuice on 2005-12-22
Hey, everyone. I just built a new computer and while it has had many problems, I'm mostly happy. Today, I tried to install Ubuntu Linux 5.10 (Breezy Badger) on it. I had to leave mid-install, and when I came back there was just a black screen. I restarted the computer, and GRUB came up nicely and I booted. After it booted, it gave me an error that said the XServer failed to start up. It dropped me in a console, but of course I had no graphical display. I'm not a complete Linux dummy, but I've never really had to troubleshoot it before because Ubuntu worked flawlessly on my old computer. Does anyone know how to fix this? Here are my specs:

Case-Coolermaster Wave Master TAC-T01-E1C
Mainboard-eVGA Socket 939 133-K8-NF41
RAM-OCZ Platinum Revision 2 1GB (2x512MB) OCZ4001024ELDCPER2-K
Processor-AMD 3800+ Venice ADA3800BPBOX
Video Card-eVGA 7800GT 256-P2-N518
Hard Drive-Seagate Barracuda SATA 3Gb/s (I can't remember if it's 120GB or 160GB, so it's either ST3160812AS or ST3120813AS)
CD/DVD Combo Drive-A good Memorex one I got at Fry's
Power Supply-Thermaltake 560W W0023R

Thanks in advance!

---

### Post by codejunkie on 2005-12-22
[QUOTE=DeathOnJuice]Hey, everyone. I just built a new computer and while it has had many problems, I'm mostly happy. Today, I tried to install Ubuntu Linux 5.10 (Breezy Badger) on it. I had to leave mid-install, and when I came back there was just a black screen. I restarted the computer, and GRUB came up nicely and I booted. After it booted, it gave me an error that said the XServer failed to start up. It dropped me in a console, but of course I had no graphical display. I'm not a complete Linux dummy, but I've never really had to troubleshoot it before because Ubuntu worked flawlessly on my old computer. Does anyone know how to fix this? Here are my specs:

Case-Coolermaster Wave Master TAC-T01-E1C
Mainboard-eVGA Socket 939 133-K8-NF41
RAM-OCZ Platinum Revision 2 1GB (2x512MB) OCZ4001024ELDCPER2-K
Processor-AMD 3800+ Venice ADA3800BPBOX
Video Card-eVGA 7800GT 256-P2-N518
Hard Drive-Seagate Barracuda SATA 3Gb/s (I can't remember if it's 120GB or 160GB, so it's either ST3160812AS or ST3120813AS)
CD/DVD Combo Drive-A good Memorex one I got at Fry's
Power Supply-Thermaltake 560W W0023R

Thanks in advance![/QUOTE]
try running these commands from the terminal 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
should auto detect and setup the xserver
if that dosn't work run this command 
```
sudo dpkg -reconfigure xserver-xorg
```
with this one you have to manually setup the xserver. under the driver section try changing the driver to vesa or nv after you make any changes to the xserver you have to restart it by either rebooting or running this command
```
sudo /etc/init.d/gdm restart
```if your using ubuntu
if your using kubuntu use this
```
sudo /etc/init.d/kdm restart
``` keep me posted if this works.

---

### Post by DeathOnJuice on 2005-12-23
Sorry, I would tell you if it worked, but I'm having other computer problems right now and I had to take Linux off. As soon as I sort my other problems out, I'll put Linux back on, but that will be a while.

---

### Post by bonzodog on 2005-12-23
I know what your problem is.

The Nvidia 7800 is unsupported in ubuntu by xorg at present and it is only supported by the last series of nvidia 3D drivers. what you will need to do first is tell xorg to use the vesa driver to start with by editing /etc/X11/xorg.conf and changing the driver line to "vesa" instead of  "nv". After you have a crappy but working X front end, you will need to download the drivers as of 7676 and up.
Breezy currently uses 7667. Install the kernel sources, then run the nvidia installer. You should now have a fully working 3D enabled front end.

---

### Post by DeathOnJuice on 2005-12-24
For future reference (when I reinstall Ubuntu), how would I go about installing the kernel sources and running the NVidia installer? As I said, I don't have much experience in Linux debugging. Sorry about that.

---

### Post by DeathOnJuice on 2005-12-24
Bump.

---

### Post by codejunkie on 2005-12-25
[QUOTE=DeathOnJuice]For future reference (when I reinstall Ubuntu), how would I go about installing the kernel sources and running the NVidia installer? As I said, I don't have much experience in Linux debugging. Sorry about that.[/QUOTE]
you could try ```
sudo apt-get install nvidia-glx nvidia-settings
```this should install the nvidia driver but if you have any problems with it and you wan't to install the latest one from [www.nvidia.com](www.nvidia.com) you can run 
```
sudo apt-get install linux-headers-`uname -r` build-essential gcc-3.4
```to install the kernel headers and other things that you need to run the nvidia driver then you need to open synaptic search for nvidia completly remove any package related to nvidia except this **xserver-xorg-driver-nv** because the others conflict with the official driver then you switch to console mode with ctrl+alt+F1 login and kill any running xserver with one of these commands 
```
sudo /etc/init.d/gdm stop
```for the gnome desktop or
```
sudo /etc/init.d/kdm stop
```for the kde desktop
then switch to root with this 
```
sudo su
```
then
```
export CC=gcc-3.4
```
now you can run the nvidia installer with 
```
sh NVIDIA-Linux-Version.run
```
and the last thing you have to do is edit your /etc/X11/xorg.conf file and change the driver to "nvidia".

---

