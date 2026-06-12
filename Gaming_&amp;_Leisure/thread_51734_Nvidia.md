---
title: "Nvidia"
date: 2005-07-25
forum: Gaming &amp; Leisure
---

### Post by storybookhero on 2005-07-25
ok I know I've asked before...but I need to know again how do I install the Nvidia Driver...step by step. any help will be greatly appreciated

---

### Post by codejunkie on 2005-07-25
[QUOTE=storybookhero]ok I know I've asked before...but I need to know again how do I install the Nvidia Driver...step by step. any help will be greatly appreciated[/QUOTE]
```
sudo apt-get install nvidia-glx nvidia-settings
``` installs the one in synaptic then you have to enable it with ```
nvidia-glx-config enable
``` then ```
sudo gedit /etc/X11/xorg.conf
``` comment out or remove the lines 
```

Load "dri"
Load "GLCore"

```
save the file and restart the xserver.

---

### Post by codejunkie on 2005-07-25
*And if your wanting to install the official nvidia driver from [www.nvidia.com](www.nvidia.com) here's a guide i wrote to do so but [COLOR=Red]you do this at your own risk[/COLOR] because i've only tested this on my hardware which is kinda old i know it works on mine but it might not on yours so if it doesn't work don't blame me because i told ya so.*

install the nvidia driver from scratch.

Find what kernel is listed when you type ```
uname -a
``` at the terminal for example mine displays ```
Linux ubuntu [COLOR=Red]2.6.10-5-k7[/COLOR] #1 Fri Jun 24 18:51:20 UTC 2005 i686 GNU/Linux
``` what l've listed in red is what to look at so  on mine i need the kernel headers for the k7 kernel. the easiest way to install these is using synaptic click on search and type headers it will list all the header packages avaliable so i install the package linux-headers-k7 these are the ones for my kernel. if you have a different kernel for example 2.6.10-5-386 you will need the package linux-headers-386 etc. you also need the build-essential package installed this provides the basic compilers and stuff used to build the kernel modules. if you can't get X running to use synaptic you can also install the kernel headers and build essential package like this. 
```
sudo apt-get update
sudo apt-get install linux-headers-386 
sudo apt-get install build-essential
```
for this example im using the 2.6.10-5-386 kernel because it's what ubuntu installs by default and the NVIDIA-Linux-x86-1.0-7667-pkg1.run nvidia driver from [www.nvidia.com](www.nvidia.com).

now to install the driver if your already in an x session exit it by hitting
```
ctrl+alt+F1
```
now at the terminal login and type:
```
sudo -s
```
enter you password 
```
telinit 3
```
if your using ubuntu
```
killall gdm
```
if your using kubuntu
```
killall kdm
```
cd to where the nvidia package is installed in this example i've placed it in /home/username/
```
cd /home/username
```
now run the installer with
```
sh NVIDIA-Linux-x86-1.0-7667-pkg1.run
```
after the installer has finished completely you need to edit your /etc/X11/xorg.conf
file and tell it to use the nvidia driver with.
```
nano /etc/X11/xorg.conf
```
example: find the line that looks like this
```

Section "Device"
        Identifier      "NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
        [COLOR=Red]Driver[/COLOR]          [COLOR=Blue]"vesa"[/COLOR]
        BusID           "PCI:1:0:0"
EndSection

```
and replace whatever is listed under the [COLOR=Red]Driver[/COLOR] section with [COLOR=Blue]"nvidia"[/COLOR] save the /etc/X11/xorg.conf file and reboot.

---

### Post by eepiccolo on 2005-08-06
Love the guide on the 7667 driver install.  Very useful.  I'd like to mention, though, that when I did it, when editing xorg.conf, I removed the line 'Load "dri"', as instructed in the NVIDIA readme.  I don't know what difference it makes, but the driver seemd to be working after installing it.  ~7500 FPS on a 5200FX, 1.7 GHz cel.

---

### Post by grofaz on 2005-08-07
I don't know. I'm leary of installing anything outside synaptic or apt-get anymore. When I tried this recipe I got segmentation faults so I ended up reinstalling ubuntu...again.

---

### Post by Jet2k5 on 2005-08-07
I'm in the process of buying a 6800GT PCI-e, and I was wondering if there is any kind of special hacks to xorg.conf for pci-express cards.  I know for example in AGP there is one called " AGP " mode or something of that sort.

If there is something for pci-express please let me know.

---

### Post by eepiccolo on 2005-08-07
[QUOTE=grofaz]I don't know. I'm leary of installing anything outside synaptic or apt-get anymore. When I tried this recipe I got segmentation faults so I ended up reinstalling ubuntu...again.[/QUOTE]
I got segmentation faults, but it was after first installing the apt-get nvidia drivers.  Installing the 7667 drivers without first installing the apt-get drivers ran without a hitch.

---

