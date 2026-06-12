---
title: "Toshiba P25-S670 /w Ubuntu Feisty /Beryl Install instructions"
date: 2007-04-23
forum: Desktop Effects &amp; Customization
---

### Post by eqspec on 2007-04-23
[B]Beryl on Ubuntu Feisty on Toshiba P25-S670 Satellite
nVIDIA G-Force FX500 128MB[/B]

If you have a P25-S670 then you know all the specs, and if you have a P4 with HT then you know that, with Ubuntu, Hyper-threading doesn't work.

These instructions are for a Toshiba Satellite P25-S670 with nVIDIA G-Force FX500 
Anyone see any problems, feel free to update.

[B]!!Don't activate the restricted driver that Ubuntu 7.04 provides!!
[/B]
First install the latest nVIDIA driver for your video card.
I used NVIDIA-Linux-x86-1.0-9755-pkg1.run from the nVIDIA site. Use it, it works.
Download that and install it. I won't go through this whole process here, but if you need help, ask.
You will need to download and install these packages, in order to install the driver. Use Synaptic Package Manager.

Files:
libc6-dev
linux-source-(kernel version installed) if you don't know, then ( uname -sr ).
linux-headers-(kernel version installed)

After you install nVIDIA driver, back up and configure X.Org
Open a terminal 
sudo gedit /etc/X11/xorg.conf
***note*** Make sure your Default Depth is 24, if not change it when you edit your xorg.conf.
Edit the following sections:
Section
"ServerLayout" Option "AIGLX" "on"
"Screen"       Option "AddARGBGLXVisuals" "True" (place this under Default Depth   24) 
                       Option "XAANoOffscreenPixmaps" (if not there already also place under Depth  24)

Save and exit gedit.
Restart X Server. Ctrl+Alt+backspace or reboot.

Ok, ready to install Beryl.

1. Open a terminal and run these commands:
	echo "deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main" | sudo tee -a /etc/apt/sources.list
        echo "deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main" | sudo tee -a /etc/apt/sources.list
        wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -

Install Beryl
sudo apt-get update
sudo apt-get install beryl beryl-manager emerald-themes

Restart X Server or reboot.
Run beryl-manager.
If everything went well you should be able to spin the cube and have window decorations, also, you should be able to change emerald themes.

If using Gnome, then add beryl-manager to Startup Programs in Sessions.

That is all. Hope this works.

---

