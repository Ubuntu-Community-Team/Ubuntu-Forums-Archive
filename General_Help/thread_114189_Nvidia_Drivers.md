---
title: "Nvidia Drivers"
date: 2006-01-08
forum: General Help
---

### Post by patchgonebad on 2006-01-08
I am new too linux, and love ubuntu.  That being said, I am peeved that installing a video driver, something so simple in other OS's is so difficult.  I am not blaming ubuntu for this at all...

Nvidia makes it damn difficult.  I read some of the 60 page howto install the drivers here and was just wondering if there is a way to get an autoupdate feature that would install the latest nvidia drivers and in the end make my cafe mocha in the morning taste a bit better.

The latest Nvidia file I have is the NVIDIA-Linux-x86-1.0-8178-pkg1.run file.  Does anyone have some very simple instructions on how to do this?

---

### Post by Azriphale on 2006-01-08
What you are probably looking for is something like:

Open up synaptic and look for:
nvidia-glx
nvidia-settings

then look for linux-restricted-modules. 
If you have not installed a different kernel (or don't know what I mean), select linux-restricted-modules-386 (for x86 PC), or, if you have installed a different kernel, select the one that matches the kernel you installed. I am assuming you are running Ubuntu for 32-bit x86 PC.

Install those and close Synaptic.
Open up a terminal and type into it:
```
sudo nvidia-glx-config enable
```
It will ask for your password and then will enable the 7667 nvidia driver.

To start using it, you need to restart the window manager. Hit ctrl+alt+del to do this. If you don't see the nvidia startup logo, try restarting your computer. 
If the graphical interface does not start, then log on in the console you get dumped on and type
```
sudo nvidia-glx-config disable
```
to get back to the free driver.

---------------------

That is to use the driver provided by Ubuntu. To use the 8178 requires a little more input. You will also need to reinstall it every time Ubuntu provides a kernel update.

I am not entirely certain of these steps, I did this a fair while ago. If it fails, you should be able to switch your xorg driver back to the "nv" driver to use X.

in synaptic, you need to do the following:
you need to have the linux-headers installed (and any specific to your kernel, i.e. i need linux-headers-686-smp). If you have not changed your kernel, get linux-headers with "386" stuck on the end.
get build-essential
you need gcc-3.4
you need to REMOVE nvidia-glx
REMOVE nvidia-settings
REMOVE linux-restricted-modules (whichever variation you have installed)

hit apply to make the changes, then close synaptic.

hit ctrl+alt+backspace to restart X.
hit ctrl+alt+F1 to get to a virtual console and log in

change to the directory where the nvidia driver you downloaded from nvidia is on you drive (for example ~/Download [~ is the syntax for home directory])

make sure the nvidia driver file downloaded from nvidia is executable

stop the display manager and install the driver.

```
cd ~/Download 
chmod +x NVIDIA-Linux-x86-1.0-8178-pkg1.run 
sudo /etc/init.d/gdm stop 
CC=gcc-3.4 sudo ./NVIDIA-Linux-x86-1.0-8178-pkg1.run
```

change the driver in your xorg.conf from "nv" to "nvidia". to do this:

```
sudo nano /etc/X11/xorg.conf
```

scroll down and look for the line that says
```
Section "Device"
```
just underneath that, change the line that reads
```
Driver "nv"
```
to
```
Driver "nvidia"
```
It should now look something like
```
Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "nvidia"
BusID "PCI:1:0:0"
```

hit Ctrl+x to exit the editor, it will ask if you want to save, press Y for yes, and hit enter for the same filename.

now, run
```
sudo /etc/init.d/gdm start
```
wait for a few seconds for it to kick off and then hit Ctrl+alt+F7 to switch back to the graphical interface.

I think that should do it. If I remember correctly. It is suggested that new users use the precompiled driver provided in Synaptic (method 1, the 7667 driver), but I think its not too hard to install the latest driver.

---

### Post by Thirsteh on 2006-01-08
Nvidia-glx is the repackaged version of Nvidia's latest or semi-latest drivers. It is recommended that you stick with those for optimal and seamless future upgrades.

Installing the nvidia drivers is a bit easier than what is explained above, however the above answer is a bit more detailed, oh well:


sudo apt-get install nvidia-glx nvidia-settings

Edit your /etc/X11/xorg.conf - change "nv" to "nvidia"

Reboot your computer, or restart X (killall gdm will do it)

Taddaa!

---

### Post by patchgonebad on 2006-01-08
Will this allow me to have dual monitor support?  I would like the desktop to span the  two screens.

---

### Post by zappa86 on 2006-01-08
Most of your nvidia settings can be acced from the nvidia-settings panel.

---

### Post by Azriphale on 2006-01-08
I spent many hours fumbling with this the first time. Don't know why, its fairly simple....
 I hope it help you.

First, you need to know the horizontal sync rate and vertical refresh rate of your second monitor. You should be able to find that in the monitor manual, or, failing that look it up on the manufacturers website, or, failing that, search on google.

by the way, after installing the nvidia driver, you also need to do this:

in you xorg.conf file, find the section that looks something like this:

```

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

```
somewhere before EndSection, add a line that reads
```
Load	"glx"
```

Now for twinview.

look for this section
```

Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

```
change it so that it looks like this (substitute the correct values for your second monitor)

```

Section "Device"
	Option		"TwinView"
	Option		"MetaModes" "1280x1024,1280x1024"
	Option		"SecondMonitorHorizSync" "22-82" 
	Option		"SecondMonitorVertRefresh" "50-76" 
	Identifier	"NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
	Driver		"nvidia" ###
	BusID		"PCI:1:0:0"
EndSection

```

It is very important to make sure you change the values of "SecondMonitorHorizSync" and "SecondMonitorVertRefresh" to the correct horizontal sync rate and vertical refresh rate of your second monitor.

nvidia describes the metamodes option like this:
A single MetaMode describes what mode should be used on each display device at a given time. Multiple MetaModes list the combinations of modes and the sequence in which they should be used.

for example: Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"

or 
Option "MetaModes" "1280x1024,1024x768; 1024x768,1024x768"
if your second monitor can't go higher than 1024x768. You can also put NULL in place of a resolution to disable any monitor in certain combinations.

That should be all there is to it.

You can find detailed descriptions in nvidia's readme on their linux driver download page.

Attached is my xorg.conf for reference. Don't worry about the extra options I have. Even the "RenderAccel" option is experimental....

---

### Post by patchgonebad on 2006-01-08
[QUOTE=zappa86]Most of your nvidia settings can be acced from the nvidia-settings panel.[/QUOTE]


**zappa86**  - I apologize, I am new to the ballgame.  Where is this panel located?  I have System/Preferences/Screen Resolution in my menu only.
[B]
Azriphale[/B] - that is great info.  In theory this would allow spanning of the desktop and 2560x1024?

And this might be a dumb question, but when running games, will they also span, or will the appropriate emulator adjust for one screen (hoping that is the case).

Thanks again guys, you have been a tremendous help.

---

### Post by ardchoille on 2006-01-08
[QUOTE=Azriphale]What you are probably looking for is something like:

Open up synaptic and look for:
nvidia-glx
nvidia-settings

then look for linux-restricted-modules. 
If you have not installed a different kernel (or don't know what I mean), select linux-restricted-modules-386 (for x86 PC), or, if you have installed a different kernel, select the one that matches the kernel you installed. I am assuming you are running Ubuntu for 32-bit x86 PC.

Install those and close Synaptic.
Open up a terminal and type into it:
```
sudo nvidia-glx-config enable
```
It will ask for your password and then will enable the 7667 nvidia driver.

To start using it, you need to restart the window manager. Hit ctrl+alt+del to do this. If you don't see the nvidia startup logo, try restarting your computer. 
If the graphical interface does not start, then log on in the console you get dumped on and type
```
sudo nvidia-glx-config disable
```
to get back to the free driver.

---------------------

That is to use the driver provided by Ubuntu. To use the 8178 requires a little more input. You will also need to reinstall it every time Ubuntu provides a kernel update.

I am not entirely certain of these steps, I did this a fair while ago. If it fails, you should be able to switch your xorg driver back to the "nv" driver to use X.

in synaptic, you need to do the following:
you need to have the linux-headers installed (and any specific to your kernel, i.e. i need linux-headers-686-smp). If you have not changed your kernel, get linux-headers with "386" stuck on the end.
get build-essential
you need gcc-3.4
you need to REMOVE nvidia-glx
REMOVE nvidia-settings
REMOVE linux-restricted-modules (whichever variation you have installed)

hit apply to make the changes, then close synaptic.

hit ctrl+alt+backspace to restart X.
hit ctrl+alt+F1 to get to a virtual console and log in

change to the directory where the nvidia driver you downloaded from nvidia is on you drive (for example ~/Download [~ is the syntax for home directory])

make sure the nvidia driver file downloaded from nvidia is executable

stop the display manager and install the driver.

```
cd ~/Download 
chmod +x NVIDIA-Linux-x86-1.0-8178-pkg1.run 
sudo /etc/init.d/gdm stop 
CC=gcc-3.4 sudo ./NVIDIA-Linux-x86-1.0-8178-pkg1.run
```

change the driver in your xorg.conf from "nv" to "nvidia". to do this:

```
sudo nano /etc/X11/xorg.conf
```

scroll down and look for the line that says
```
Section "Device"
```
just underneath that, change the line that reads
```
Driver "nv"
```
to
```
Driver "nvidia"
```
It should now look something like
```
Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "nvidia"
BusID "PCI:1:0:0"
```

hit Ctrl+x to exit the editor, it will ask if you want to save, press Y for yes, and hit enter for the same filename.

now, run
```
sudo /etc/init.d/gdm start
```
wait for a few seconds for it to kick off and then hit Ctrl+alt+F7 to switch back to the graphical interface.

I think that should do it. If I remember correctly. It is suggested that new users use the precompiled driver provided in Synaptic (method 1, the 7667 driver), but I think its not too hard to install the latest driver.[/QUOTE]
Thank you very much for simplifying this matter. This is great help :)

---

### Post by Azriphale on 2006-01-08
you can get to nvidia-settings by simply typing that into the console. It may also be in a menu somewhere, but I don't know.

The TwinView configuration that the nvidia driver uses makes most applications monitor aware, and stops things from opening right in the centre.

Most games you will have to run in a window, I think, because they usually open  in fullscreen mode, in the very centre, split across both monitors. I don't yet know how to fix this tho. One way you can do it is by enabling a second MetaMode, something like "1280x1024, NULL", so the full metamode line would become:
```
Option      "MeteModes"     "1280x1024,1280x1024; 1280x1024,NULL"
```

You could switch to the second mode to disable your second monitor for games, and switch back afterwards. But I think thats too much if you switching a lot. I just make games run in a window, which can usually be achieved with a "Alt+Enter"

---

